---
title: "Bash script project - Need people to contribute"
date: 2014-03-22
forum: The Cafe
---

### Post by Tristan_Williams on 2014-03-22
I need people to help me improve a bash script.

I am creating a bash script that will serve as an automated system maintenance and backup tool, mainly for Ubuntu beginners.

The script can perform backup of the /home directory, maintain packages through apt-get, and maintain PPAs.

Here is the first version of the script:
```

#!/bin/bash

# This is the nls-maintain script
# This is used on NLSLinux systems for basic system maintenance.
# This was developed by Tristan Williams, Owner of Newlife Linux Solutions
# This script is free and open source software
# Feel free to change it any way you like



function nls_main {

    read -p "Confirm you want to run maintenance [y/n] " nls_conf

        if [ "$nls_conf" == "y" ]; then
            unset nls_conf
            nls_maintain
        elif [ "$nls_conf" == "n" ]; then
            unset nls_conf
            exit
        else
            unset nls_conf
            nls_err_msg
        fi
}

# Function for system maintenance
function nls_maintain {

    clear
    
    # Ask user if they want to do a system backup before maintenance
    read -p "Perform system backup before maintenance? [y/n] " nls_bkup_yn
        if [ "$nls_bkup_yn" == "y" ]; then
            # Determine drive to hold backup
            read -p "Backup to which drive? (example: sdb1)" nls_bkup_drive
            
            # Mount backup drive
            mount -v $nls_bkup_drive /mnt/
            
            # Remove previous backup, so that old files aren't kept
            sudo rm -rf /mnt/nls_bkup/
            
            # Re-make backup directory on backup drive
            sudo mkdir /mnt/nls_bkup/
            
            # Copy home folders to backup drive
            sudo cp -Rv /home/ /mnt/nls_bkup/
            
            # Unmount backup drive to avoid issues with file managers later
            sudo umount -v $nls_bkup_drive
            
            # Inform user of backup location
            echo "Backups are stored in the drive which you specified, in a directory named nls_bkup"
            echo ""
            read -p "Press any key to start maintenance"
            
            # Unset old variables
            unset nls_bkup_drive
            unset nls_bkup_yn
            
            nls_no_bkup_maintain
        elif [ "$nls_bkup_yn" == "n" ]; then
        
            # Unset old variables
            unset nls_bkup_drive
            unset nls_bkup_yn
            
            nls_no_bkup_maintain
        else
            unset nls_bkup_yn
            nls_loc="nls_maintain"
            nls_err_msg
        fi
    
    # Maintenance
    function nls_no_bkup_maintain {
    
        clear
        
        # Determine if user wants to check for broken PPAs
        read -p "Check for broken PPAs? [y/n] " nls_maintain_ppa_check
            # Check for broken PPAs
            if [ "$nls_maintain_ppa_check" == "y" ]; then
                
                clear
                echo "Checking for broken PPAs... "
                sudo apt-get update > update_app.txt
                clear
                cat update_app.txt | grep Err | cut -c 12- > broken_app.txt 

                IFS=$'\n' read -d '' -r -a lines < broken_app.txt
                 
                 # List broken PPA(s)
                echo "Found the following broken ppa's"
                echo "${lines[@]}"
                echo ""
                echo "If there are no PPAs listed above, reply 'n'"
                echo "to the prompt below"
                echo ""
                echo "It may be that the repositories are down and will be up later"
                echo "If you continue these will be deleted from your system"

                read -p "Remove files? [y/n] " cont_1
                    # If yes, remove broken PPA(s) from system
                           if [ "$cont_1" == "y" ]; then
                            clear
                            cat update_app.txt | grep Err | cut -c 12- | cut -d ' ' -f 1 > broken_app.txt 
                            IFS=$'\n' read -d '' -r -a lines < broken_app.txt
                            i="0"

                            while [[ "${lines[$i]}" != "" ]]; do
                                     grep -H "${lines[$i]}" /etc/apt/sources.list.d/*.list | cut -d ':' -f 1  > delete_app.txt
                                    IFS=$'\n' read -d '' -r -a linesd < delete_app.txt
                                    a="0"
                        
                                    while [[ "${linesd[$a]}" != "" ]]; do

                                        file="${linesd[$a]}"
                                        if [ -f "$file" ]; then
                                            clear
                                                echo "$file will be removed."
                                            read -p "Continue with removal? [y/n] " cont_2
                                            # If yes, remove $file
                                                if [ "$cont" == "y" ]; then
                                                        clear
                                                          echo "Removing $file";
                                                          sudo rm "$file"
                                                        sleep 5
                                                else
                                                          echo "Will keep $file";
                                                        sleep 5
                                                fi
                                        else
                                            clear
                                                echo "$file not found."
                                            sleep 5
                                        fi

                                        echo "${linesd[$a]}"
                                        a=$[$a+1]
                                    done
                   
                                i=$[$i+1]
                            done
                        elif [ "$cont_1" == "n" ]; then
                            clear
                            echo ""
                        fi
                clear
                rm update_app.txt
                rm broken_app.txt
                rm delete_app.txt
                
                # Unset old variables
                unset nls_maintain_ppa_check
                unset IFS
                unset cont_1
                unset cont_2
                unset file
                
            # Do not check, continue with maintenance    
            elif [ "$nls_maintain_ppa_check" == "n" ]; then
                unset nls_maintain_ppa_check
                echo "Not checking for broken PPAs"
            fi
        
        # System Maintenance
        clear
        sudo apt-get update
        sudo apt-get upgrade
        sudo apt-get install -f
        sudo apt-get upgrade
        sudo apt-get autoclean
        sudo apt-get autoremove
    
    }

    nls_init_menu

}
# Function for invalid menu selection error message
#
# This will happen if, for example, there are menu options 1, 2, 3, and 4, but the user
# selects option 5. There isn't an option 5, so the user will get this error message, and
# will be returned to the previous location to re-select a valid option
function nls_err_msg {

    clear
    echo "The option you chose is not valid. You must select a valid menu entry"
    sleep 2
    echo "You will be returned to your previous location, at which point, you will select"
    echo "a valid entry"
    echo ""
    read -p "Press any key to continue... "
    $nls_loc

}



# Developers:
#
#
# Tristan Williams    |    tristan401_2000@live.com
# Main script writer

# Changelog:
#
# 1 -    Initial script creation
# 2 -    


```



As people contribute improvements to the script, I will have the updated script below:



Thank you all.

---

### Post by TheFu on 2014-03-22
Specify full paths to every command - always. This is rule #1 to scripting. It is a security thing AND a way to ensure someone with a strange PATH doesn't get screwed running the script.

Hardcoding filenames is poor for maintainability.  Just like with program executables, it is best to set variables for those things in the beginning of the script. There are millions of examples of this.  Here's a link to one of mine: [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt)

Add a license so people know how you are willing for the code to be used. Nothing fancy is needed, but if you want the program to be used everywhere, some companies have specific policies which allow certain licenses and reject others.

Debian has recommended **aptitude** over apt-get for years.

There are a few **traps** I'd want to handle different signals at unexpected times of the script too.

I'll keep the programming style comments to myself. ;)

---

### Post by lykwydchykyn on 2014-03-22
Just a suggestion, it might be easier for people to contribute to something like this if you put it on github or a similar code-collaboration site.

---

### Post by ian-weisser on 2014-03-22
I have real heartburn about encouraging beginners to use PPAs...the source of most package manager problems.

I'm not sure about the apt maintenance section. What kinds of issues it it supposed to solve?

*apt-get update* is already run by a daily cron job (/etc/cron.daily/apt)
*apt-get upgrade* is already run by the same cron job if the user's apt-conf settings are correct.
I find *apt-get install -f* to be only occasionally useful, and more frequently confusing to users than helpful.
I suspect that *apt-get autoclean* does something rather different than you expect. Again, it's already automatically done by the the daily cron job if the user hasn't been mucking with apt-conf settings.
*apt-get autoremove* can be done by the daily cron job. The settings have it turned off to prevent essential packages from getting autoremoved in error. It might be easier to simply enable it than to make it part of this script.

---

### Post by papibe on 2014-03-22
Hi Tristan_Williams.

I would remove all sudos from your script, and code it assuming it will be run as root:
```
sudo yourscrip.sh
```
You could check at the beginning of the script if it's being run as root:
```
#!/bin/bash

# Obtain current effective user ID.
CURRENT_EUID=$(id --user)

# Quit if the script is not being run by root.
if [ "$CURRENT_EUID" -ne 0 ]; then
    echo "$0 must be run as root. Example: sudo $0"
    exit 1
fi

```
Just my thoughts.
Regards.

---

### Post by Erik1984 on 2014-03-23
- Move the code to github, launchpad or another code hosting service with syntax highlighting for bash.
- Split the functionality in multiple files or use more small functions. This reduces the visual complexity of function like nls_no_bkup_maintain with deep nesting.

---

### Post by TheFu on 2014-03-23
github would be preferred by more people outside Ubuntu than launchpad.  For example, I do not have a launchpad account, but I do have github, which I don't use.  I prefer to host my own git repo and share it as necessary, but for something like this - github would be preferred, probably.  There are other options too - bitbucket.

Any function longer than 1 screen is TOO long. Simplify.  That means 20 lines or less, including comments. Longer functions have been proven to hide bugs in other languages - don't know about bash.

---

### Post by srikailash on 2014-05-08
a new function whick checks wheather the available space in the drive entered by the user has enough available space to back up the files.This can be called after the drive name is entered.
function goes something like this::

```
function nls_checkspace {
wanted_space=$(df -h | awk '{if ($1 == "home folder path") print $4}')
avail_space=$(df -h | awk '{if ($1 == "backup drive path") print $4}')
#compare wanted space and available space
}
```

---

