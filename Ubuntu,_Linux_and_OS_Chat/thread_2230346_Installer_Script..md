---
title: "Installer Script."
date: 2014-06-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Tadaen_Sylvermane on 2014-06-18
```
#!/bin/bash
#Tadaen Sylvermane
#Ubuntu installer
#Version 1.0
#Created 2014.6.18 @ 1418
#Last Edit 2014.6.18 @ 1515

# Notes : IMPORTANT ###############################################################################
#
# This script requires a pre-made Ubuntu folder somewhere on your hard drive, or a mounted flash drive
# to draw from. This folder holds config files, tar.gz files, and your backed up /var/cache/apt/archives if
# you so desire. The folder structure needs to be as follows.
#
# Ubuntu Folder --------
#            |
#            |------- cache folder---
#            |            |------- backed up /var/cache/apt/archives debs
#            |
#            |------- configs folder-
#            |            |------- ubuntuapt (list of packages to install from repos)
#            |            |------- ubuntuppa (list of ppas to add)
#            |
#            |------- debs folder----
#            |            |------- downloaded debs (packages not from repos)
#            |
#            |------- icons folder --
#            |            |------- icon tar.gz packs
#            |
#            |------- themes folder -
#                        |------- theme tar.gz packs
#
###################################################################################################

##### begin script #####

### user functions ###

servermnt() { # create folder for mountpoint in ~
    servermnt_1 () { # local function to do the work
        clear && read -p "Enter name of folder to create in /home/$USER --> " serveropt1
        read -p "You entered $serveropt1, Is this correct? (y / n)" serveropt2
        if [[ "$serveropt2" == [Yy] ]] ; then
            if [[ ! -d "/home/$USER/$serveropt1" ]] ; then
                mkdir -p "/home/$USER/$serveropt1"
                if [[ ! -f "/home/$USER/folder.log" ]] ; then
                    echo "Created folder $serveropt1" >> "/home/$USER/folder.log"
                fi    
                servermnt
            else
                echo "Directory already exists."
                sleep 2
                servermnt
            fi
        else
            echo "Try again..."
            sleep 2
            servermnt
        fi
    }
    # if log exists prints it out on screen before prompt
    if [[ -f "/home/$USER/folder.log" ]] ; then
        clear && echo "Folders already created... "
        cat "/home/$USER/folder.log"
    fi
    # prompt to control the entire function
    echo
    read -p "Do you want to create a mountpoint / folder? (y / n) --> " serveropt0
    if [[ "$serveropt0" == [Yy] ]] ; then
        servermnt_1
    fi
    # clean up log file
    if [[ -f "/home/$USER/folder.log" ]] ; then
        rm "/home/$USER/folder.log"
    fi
}

minecraft() { # set up minecraft
    minecraft_1() { # local function to do the work
        # create shortcut
        clear && read -p "Enter path to Minecraft source folder --> " mcshortopt1
        if [[ -d "$mcshortopt1" ]] ; then
            if [[ -f "$mcshortopt1/Minecraft.desktop" ]] ; then
                if [[ ! -d "/home/$USER/.local/share/applications" ]] ; then
                    mkdir -p "/home/$USER/.local/share/applications"
                fi
                cp "$mcshortopt1/Minecraft.desktop" "/home/$USER/.local/share/applications"
            fi
            # insert resource packs
            if [[ ! -d "/home/$USER/.minecraft/resourcepacks" ]] ; then
                mkdir -p "/home/$USER/.minecraft/resourcepacks"
            fi
            find "$mcshortopt1" -iname '*.tar.gz' -exec tar -xf {} -C "/home/$USER/.minecraft/resourcepacks" \;
        else
            echo "Folder doesn't exist, try again."
            sleep 2
            minecraft
        fi
    }
    # prompt to control the entire function
    clear && read -p "Do you want to setup Minecraft? (y / n) -->" mcshortopt0
    if [[ "$mcshortopt0" == [Yy] ]] ; then
        minecraft_1
    fi
}

### general functions ###

backups() { # check if file exists, then check if backup doesn't exist
    # if both true then make backup | $1 is file to make backup of
    [[ -s "$1" ]] && [[ ! -s "$1.bak" ]] && cp "$1" "$1.bak"
    echo "Backed up $1" >> /tmp/backups.log
}

backups_1() { # backup requested files
    backups_2()    { # local function to do the work
        clear && read -p "Enter path of file to backup --> " backupsopt1
        if [[ -s "$backupsopt1" ]] ; then
            if [[ ! -s "$backupsopt1.bak" ]] ; then
                backups "$backupsopt1"
                echo "File backed up"
                sleep 2
                backups_1
            else
                echo "Backup already exists."
                sleep 2
                backups_1
            fi
        else
            echo "File doesn't exist"
            sleep 2
            backups_1
        fi
    }
    # if log exists prints it out on screen before prompt
    if [[ -f /tmp/backups.log ]] ; then
        clear && echo "Files already backed up..."
        echo
        cat /tmp/backups.log
    fi
    # prompt to control entire function
    echo
    read -p "Would you like to backup anything? (y / n)" backupsopt0
    if [[ "$backupsopt0" == [Yy] ]] ; then
        backups_2
    fi
    # clean up log file
    if [[ -f /tmp/backups.log ]] ; then
        rm /tmp/backups.log
    fi
}

upgrade() { # debian based upgrade
    # $1 is backed up cache location | $2 is destination
    clear
    read -p "Will cause reboot. Are you sure? (y / n) --> " ugopt0
    if [[ "$ugopt0" == [Yy] ]] ; then
        sleep 1
        clear && echo "Copying cache into place if it exists. Standby..."
        find "$1" -iname '*.deb' -exec rsync {} "$2" \;
        apt-get update
        apt-get -y dist-upgrade
        reboot
    else
        echo "Do what you need to and come back later..."
        exit 1
    fi
}

setppa() { # set up ppas | $1 is file with list of ppas
    if [[ -s "$1" ]] ; then
        for i in $(cat "$1") ; do
            add-apt-repository "$i"
            echo "Added ppa $i" >> /tmp/ppa.log
        done
    fi
}

setppa_0() { # ask if more ppas to setup.
    setppa_1() { # set up requested ppas | $1 is the ppa to add.
        add-apt-repository "$1"
        echo "Added ppa $1" >> /tmp/ppa.log
    }
    setppa_2() { # local function to do the work
        clear && read -p "Enter the ppa path (i.e. ppa:whatever/whatever) --> " setppaopt1
        read -p "You entered $setppaopt1. Is this correct? (y / n) --> " setppaopt2
        if [[ "$setppaopt2" == [Yy] ]] ; then
            setppa_1 "$setppaopt1"
            echo "ppa setup!"
            sleep 1
            setppa_0
        else
            echo "Try again..."
            sleep 1
            setppa_0
        fi
    }
        
    # if log exists prints it out on screen before prompt
    if [[ -f /tmp/backups.log ]] ; then
        clear && echo "ppa's added..."
        echo
        cat /tmp/ppa.log
    fi
    # prompt to control entire function
    echo
    read -p "Would you like to add another ppa? (y / n)" setppaopt0
    if [[ "$setppaopt0" == [Yy] ]] ; then
        setppa_2
    fi
    # clean up log file
    if [[ -f /tmp/ppa.log ]] ; then
        rm /tmp/ppa.log
    fi
}

software() { # installs packages... downloaded & local |
    # $1 is path to apt list | $2 is path to downloaded debs
    apt-get update
    apt-get -y install $(cat "$1")
    if [[ -d "$2" ]] ; then
        find "$2" -iname '*.deb' -exec dpkg -i {} \;
    fi
    apt-get -fy install
    apt-get autoremove
    apt-get autoclean
}

theming() { # untar themes into appropriate locations
    # $1 is folder of tar.gz files | $2 is destination
    find "$1" -iname '*.tar.gz' -exec tar -xf {} -C "$2" \;
}

### control functions ###

check_user() { # make sure not running as root
    if [[ "$USER" == root ]] ; then
        echo "Must run as regular user."
        sleep 1
        exit 1
    fi
}

check_root() { # make sure running as root
    if [[ "$USER" != root ]] ; then
        echo "Must run as root!"
        sleep 1
        exit 1
    fi
}

user_groups() { # add users to groups
    user_add() { # local function to actually do the work
        clear && read -p "Enter user name to add to group --> " usrgropt1
        if getent passwd "$usrgropt1" ; then
            clear && read -p "Enter group for the user --> " usrgropt2
            if getent group "$usrgropt2" ; then
                adduser "$usrgropt1" "$usrgropt2"
                echo "Added $usrgropt1 to $usrgropt2" >> /tmp/users.log
                user_groups
            else
                echo "Group doesn't exist. Check again."
                sleep 2
                user_groups
            fi
        else
            echo "User doesn't exist. Check again."
            sleep 2
            user_groups
        fi
    }
    # if log exists prints it out on screen before prompt
    if [[ -f /tmp/users.log ]] ; then
        clear && echo "Users added to groups so far..."
        echo
        cat /tmp/users.log
    fi
    # prompt to control entire function
    echo
    read -p "Add user to a group? ( y / n ) --> " usrgropt0
    if [[ "$usrgropt0" == [Yy] ]] ; then
        user_add
    fi
    if [[ -f /tmp/users.log ]] ; then
        rm /tmp/users.log
    fi
}

### menus ###

rootopt() {
    rootmenu() {
        clear && echo "Enter the number of your selection."
        echo
        echo "1) Update Installation"
        echo "2) Install themes"
        echo "3) Install packages"
        echo "9) Exit installer"
        read -p "Have you decided? --> " mainopt0
        if [[ "$mainopt0" == 1 ]] ; then        
            backups /etc/apt/sources.list
            backups /etc/fstab
            upgrade "$debfolder" /var/cache/apt/archives
        elif [[ "$mainopt0" == 2 ]] ; then
            theming "$debfolder/icons" /usr/share/icons
            theming "$debfolder/themes" /usr/share/themes
            rootmenu
        elif [[ "$mainopt0" == 3 ]] ; then
            setppa "$debfolder/configs/ubuntuppa"
            setppa_0
            software "$debfolder/configs/ubuntuapt" "$debfolder/debs"
            user_groups
            rootmenu
        elif [[ "$mainopt0" == 9 ]] ; then
            clear && echo "Exiting. Thank you for using the script."
            exit 0
        else
            rootmenu
        fi
    }
    # prompt to control entire function
    check_root
    clear && read -p "Enter path to your Ubuntu folder --> " debfolder
    if [[ -d "$debfolder" ]] ; then
        rootmenu
    else
        echo "Folder doesn't exist. Check location and try again."
        exit 1
    fi
}

useropt() {
    check_user
    echo "1) Setup Minecraft?"
    echo "2) Create folder in /home/$USER ?"
    echo "9) Exit installer."
    read -p "Enter number of your choice --> " useropt0
    if [[ "$useropt0" == 1 ]] ; then
        minecraft
        useropt
    elif [[ "$useropt0" == 2 ]] ; then
        servermnt
        useropt
    else 
        echo "Thank you for using the script!"
        exit 0
    fi
}

control() { # main entry point
    echo "Welcome to your Ubuntu installer script."
    echo "This script requires a few config files already in place."
    echo "Read lines 8 - 31 of the script to get an idea."
    echo
    echo "1) Root tasks (Must be root or have used sudo to start script!)"
    echo "2) User tasks (Must NOT be root or have used sudo to start script!)"
    echo "8) Small help printout."
    echo "9) Exit installer."
    read -p "Have you decided? --> " controlopt0
    if [[ "$controlopt0" == 1 ]] ; then
        rootopt
    elif [[ "$controlopt0" == 2 ]] ; then
        useropt
    elif [[ "$controlopt0" == 9 ]] ; then
        echo "Exiting. Thank you for using the script."
        exit 0
    else
        control
    fi
}

### run script ###

control

##### end script #####
```

Reposting with apologies for being rude. Not professional by any means. Script is here if you want to use it or as a template.

---

### Post by oldos2er on 2014-06-18
Not an Ubuntu support request; moved to Ubuntu, Linux & OS Chat.

---

### Post by Tadaen_Sylvermane on 2014-06-19
Updated post + apology.

---

