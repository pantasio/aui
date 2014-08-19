# Archlinux Ultimate Install Script

Install and configure archlinux has never been easier!

You can try it first with a `virtualbox`

## Prerequisites

- A working internet connection
- Logged in as 'root'

## How to get it
### With git
- Get list of packages and install git: `pacman -Sy git`
- get the script: `git clone git://github.com/helmuthdu/aui`

### Without git
- get the script: ` wget --no-check-certificate https://github.com/helmuthdu/aui/tarball/master -O - | tar xz`
    - an alternate URL (for less typing) is ` wget --no-check-certificate http://bit.ly/NoUPC6 -O - | tar xz`
    - super short `wget ow.ly/wnFgh -o aui.zip`

## How to use
- ais mode: `cd <dir> && ./ais`
- aui mode: `cd <dir> && ./aui`

## Archlinux Install Script (ais)
- Configure keymap
- Select editor
- Automatic configure mirrorlist
- Create partition
- Format device
- Install system base
- Configure fstab
- Configure hostname
- Configure timezone
- Configure hardware clock
- Configure locale
- Configure mkinitcpio
- Install/Configure bootloader
- Configure mirrorlist
- Configure root password

## Archlinux Ultimate Install (aui)
- Backup all modified files
- Install additional repositories
- Create and configure new user
- Install and configure sudo
- Automatic enable services in systemd
- Install an AUR Helper [yaourt, packer, pacaur]
- Install base system
- Install systemd
- Install Preload
- Install Zram
- Install Xorg
- Install GPU Drivers
- Install CUPS
- Install Additional wireless/bluetooth firmwares
- Ensuring access to GIT through a firewall
- Install DE or WM [Cinnamon, Enlightenment, FluxBox, GNOME, KDE, LXDE, OpenBox, XFCE]
- Install Developement tools [Vim, Emacs, Eclipse...]
- Install Office apps [LibreOffice, GNOME-Office, Latex...]
- Install System tools [Wine, Virtualbox, Grsync, Htop]
- Install Graphics apps [Inkscape, Gimp, Blender, MComix]
- Install Internet apps [Firefox, Google-Chrome, Jdownloader...]
- Install Multimedia apps [Rhythmbox, Clementine, Codecs...]
- Install Games [HoN, World of Padman, Wesnoth...]
- Install Fonts [Liberation, MS-Fonts, Google-webfonts...]
- Install and configure Web Servers
- Many More...

If you like my work, please consider a small Paypal donation at helmuthdu@gmail.com :)

#!/bin/bash

pacman -Sy git
git clone git://github.com/pantasio/aui

#this is shell help
# sau khi phan partition
# fdisk -l
#Now is time to create disk file system and format partitions with ext4. Issue the following 

commands for ROOT and HOME partitions.

# mkfs.ext4 /dev/sda1                day la ROOT
# mkfs.ext4 /dev/sda5                day la HOME

Format and initialize SWAP partition.

# mkswap /dev/sda2
# swapon /dev/sda2

#Now run lsblk command to double check partitions and make sure everything is in correctly 

configured so far.

#For performing an Arch Linux installation the two partitions created must be mount it on 

Arch Live running system to a mount point to be accessible. For this setup I shall use the 

/mnt Arch system live path to mount ROOT partition (/dev/sda1) and /mnt/home path to mount 

HOME partition (/dev/sda5). Don’t be worried about SWAP partition (it’s has already been 

initialized above). Use the following commands in the following order for this step.

# mount /dev/sda1 /mnt
# mkdir /mnt/home
# mount /dev/sda5 /mnt/home


EDITOR # nano /etc/pacman.d/mirrorlist

## Viet Nam
#Server = http://f.archlinuxvn.org/archlinux/$repo/os/$arch
#Server = http://mirror-fpt-telecom.fpt.net/archlinux/$repo/os/$arch



#bat dau install
# pacstrap -i /mnt base base-devel

#After all packages are installed it’s time to generate fstab file for our new Arch Linux 

system to be able to boot from newly partitions with the help of the following command.

# genfstab -U -p /mnt >> /mnt/etc/fstab


#After the system reboots you will lose network connection and your Network Interface Card 

name will change. To manage this issue, login with newly created user with sudo powers and 

issue the following command to get NIC Ethernet name.
# ip link


#After you get the name of the Ethernet connection start and enable the connection on 

Ethernet NIC running the following commands.
# sudo systemctl enable dhcpcd@ens33.service
# sudo systemctl start dhcpcd@ens33.service

If you have multiple network interfaces on DHCP run the following command and verify 

connectivity issuing a ping command against google domain.
# sudo systemctl enable dhcpcd.service
















