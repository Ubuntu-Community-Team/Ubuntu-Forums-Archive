---
title: "HOW TO: Install Virtualmin, Webmin &amp; Usermin on Ubuntu Server 8.04 LTS (Easy)"
date: 2009-06-26
forum: Tips &amp; Tutorials Team
---

### Post by Francewhoa on 2009-06-26
This how to is for **absolute beginners. **An installation script will do most of the hard work for you. There're lot of steps below but that's easy.
[B] 
OBJECTIVES:[/B]
- Install and setup the following:
    - Ubuntu Server edition 8.04.2
    - Webmin 1.470 GPL
    - Virtualmin 3.69 GPL
    - Usermin 1.400 GPL

**COST IN $ US:**
$0 for the above softwares because we are going to use only Open Source softwares. 
$20 to $50 per month for the hosting.
$10 to $40 per year for a domain name.

**HOW LONG DOES IT TAKES?**
30 to 60 minutes.

**REQUIEREMENTS:**
-    One remote web hosting servers with:
                ---------        -    A freshly installed Ubuntu 8.04 LTS Server Edition 32bit version. It works too with 64 bits version. But in this how-to we will be using the 32 bits version. Ubuntu Server is a free open source operating system very performant to host websites. Ubuntu is the most popular Open Source Linux distro. Read more at [http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)
                        --------- - Apache most NOT be already installed. It will be install by the below installation script.
                        --------- - At least 512MB of RAM (memory). I never tried with less. If unsure you better install with more RAM then needed. Then reduce the RAM later.
                        --------- - At least 2GB (2048MB) of swap disk (Linux virtual memory). Once Virtualmin is installed the swap disk can be reduce to 512MB. 
                        --------- - Full root access and full SSH access. Such as most VPS, dedicated or your own server. Make sure you have root access. Shared hosting will NOT work.
                        --------- - Access to “Universe” and “Multiverse” Ubuntu repositories. Read more at [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
-    One local home computer with Ubuntu 8.04 LTS Desktop Edition 32bit version. Nothing will be hosted on this computer. It will be use to access the remote Ubuntu Server via SSH.

Connect to your remote Ubuntu server via SSH on your home computer. To do so open TERMINAL. TERMINAL can be found under Ubuntu desktop panel menu > APPLICATIONS > TERMINAL
The TERMINAL window will open. 
Type in the following command line. Then press RETURN key.
```
ssh root@123.123.123.123 
```(Note: In the above command replace “root” with your remote Ubuntu Server username and replace “123.123.123.123” with your remote Ubuntu Server IP address. This IP address is provided by your host provider. Username is usually 'root'.)
(Tips: You can copy and paste text or command line to TERMINAL using right click > Select COPY or PASTE)

You are now connected to your remote Ubuntu server.

By default a fresh Ubuntu installation comes with the Fully Qualified Domain Name (FQDN) ‘ubuntu’. But Virtualmin installation script required a third level domain name such as ‘ns1.YOURDOMAINNAMEHERE.com’.

In the following we’ll set a third level domain name.

We are now going to check the remote Ubuntu Server actual fully qualified domain name (FQDN)
Type in the following command in TERMINAL:
    ```
hostname --fqd
```Note: Make sure it’s two dash before 'fqd' not one.

If output returns ‘ubuntu’ you need to change the FQDN.

We are now going to configuring the remote Ubuntu server network.
Because the Ubuntu installer has configured our system to get its network settings via DHCP, we have to change that now because a server should have a static IP address.
Edit the file 'interfaces' located at:
    ```
/etc/network/interfaces
```Note: One way to edit a file is using your local Ubuntu Desktop and navigate to > PLACES menu > CONNECT TO SERVER >
    Service type: SSH
    Server: [type in your server IP address]
    Port: [leave empty]
    Username: [type in your username. Usually it's ”root”]
    Check ADD BOOKMARK box. So next time it's easier to connect.
    Bookmark name: [Could be anything.]
    
A new window will open. This is your remote server root folder.
Navigate to /etc/network/interfaces

We are now going to edit the file INTERFACES. To do so right click on the file and select OPEN WITH OTHER APPLICATION... > Select TEXT EDITOR > Click on OPEN button.

(Tips: It is recommended to backup any file before editing it. To do so copy and paste the file in the same directory. Then change the file copy name to “interface-backup-add_current_date_here”)

(Note: For now on we assume that you know how to open a file, backup a file and edit it.)

Edit the file INTERFACES. We are editing the last line. And will add a few new lines at the bottom.

[File before:]
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```[File after:]
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 123.123.123.123
        netmask 255.255.255.0
        network 123.123.123.0
        broadcast 123.123.123.255
        gateway 123.123.123.123
```Note: In above AFTER you must replace the numbers:
address 123.123.123.123
    (Change '123.123.123.123' to your remote Ubuntu Server IP.)

netmask 255.255.255.0
    (Paste as is. Do not change it.)

network 123.123.123.0
    (Change '123.123.123.0' to your remote Ubuntu Server IP but you must change the last number to zero '0'.)

broadcast 123.123.123.255
    (Change '123.123.123.255' to your remote Ubuntu Server IP but you must change the last number to 255'.)

gateway 123.123.123.123
    (Change '123.123.123.123' to your remote Ubuntu Server gateway address. Gateway address and IP address are different. Ask your hosting provider.)

Restart your network on your remote Ubuntu Server. 
To do so open TERMINAL and type in the following command.
    ```
/etc/init.d/networking restart
```If [COLOR=black]succes[/COLOR]sful terminal will output the following
    > * Reconfiguring network interfaces...
 [ OK ]On your remote Ubuntu Server.
Edit the file 'hosts' located at
        ```
/etc/hosts
```We are going to edit the first two lines only.

[File before:]
```
127.0.0.1    localhost
127.0.1.1    ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```[File after:]
```
127.0.0.1    localhost.localdomain    localhost
123.123.123.123    ns1.YOURDOMAINNAMEHERE.com    ns1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Note 1: In above AFTER you must keep the following line as is:
```
127.0.0.1    localhost.localdomain    localhost
```                (This line must be paste as is. Do not change it.)

            Note 2: In above AFTER you must replace the numbers:
            ```
123.123.123.123    ns1.YOURDOMAINNAMEHERE.com    ns1
```                (Change “123.123.123.123” to your remote Ubuntu server IP address.)

                  (Change “ns1.YOURDOMAINNAMEHERE.com” to your domain name. Keep the “ns1” at the beginning as is. 'ns1' is an industry standard. It stands for Name Server designator 1. Keep the “ns1” at the end as is.)

                For example if your domain name is virtualmin.com then your line would be: 
            ```
67.225.148.19    ns1.virtualmin.com    ns1
```Type in the following command in TERMINAL:
        ```
echo ns1.YOURDOMAINNAMEHERE.com > /etc/hostname
```If [COLOR=black]succes[/COLOR]sful TERMINAL will return nothing.

Type in the following command in TERMINAL:
    ```
/etc/init.d/hostname.sh start
```If [COLOR=black]succes[/COLOR]sful TERMINAL will return nothing.

Type in the following command in TERMINAL:
    ```
hostname
```If [COLOR=black]succes[/COLOR]sfull TERMINAL will output
    > ns1.YOURDOMAINNAME.comType in the following command in TERMINAL:
    ```
hostname -f
```If [COLOR=black]succes[/COLOR]sfull TERMINAL will output
    > ns1.YOURDOMAINNAME.comThe remote Ubuntu Server’s network is now configured.
The FQDN is now configured.

We are now going to change the remote Ubuntu Server Default Shell.

    If you don't do this, the ISPConfig installation will fail.

Note: A symlink is basically a shortcut to a file. Think of them like a shortcut in MS Windows, except the shortcut isn't a separate file, it's a "link" to the actual file.

Type in the following command in TERMINAL:
            ```
ln -sf /bin/bash /bin/sh
```If [COLOR=black]succes[/COLOR]sful TERMINAL will return nothing.

We are now going to disable then remove AppArmor on the remote Ubuntu Server.

Note: AppArmor is a security extension (similar to SELinux) that should provide extended security. In my opinion you don't need it to configure a secure system, and it usually causes more problems than advantages (think of it after you have done a week of trouble-shooting because some service wasn't working as expected, and then you find out that everything was ok, only AppArmor was causing the problem). Therefore I disable it (this is a must if you want to install ISPConfig later on). 

Type in the following command in TERMINAL:
```
/etc/init.d/apparmor stop
```If [COLOR=black]succes[/COLOR]sful TERMINAL will return:
        > /etc/init.d/apparmor stop Type in the following command in TERMINAL:
```
update-rc.d -f apparmor remove
```If [COLOR=black]succes[/COLOR]sful TERMINAL will output a few lines. The last 2 lines will look like this:
> Removing any system startup links for /etc/init.d/apparmor ... /etc/rcS.d/S37apparmorType in the following command in TERMINAL:
```
apt-get remove apparmor apparmor-utils
```In my case the package 'apparmor-utils' wasn't install so TERMINAL returns the following. That's normal.
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apparmor is not installed, so not removed
Package apparmor-utils is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.Type in the following command in TERMINAL:
        ```
free -m
```TERMINAL will output the amount of RAM use on your remote Ubuntu Server before. Look at the second column titled 'used' and the first line titled 'Mem:'. All number are in MB. This is before installing Virtualmin. 
In my case TERMINAL output 65MB RAM used.

To make sure all changes we made are active reboot your remote Ubuntu Server.

We are now going to check the remote Ubuntu Server new fully qualified domain name (FQDN)
Open TERMINAL. 
Login your remote Ubuntu Server.
Type in the following command in TERMINAL:
    ```
hostname --fqd
```Note: Make sure it’s two dash before 'fqd' not one.

If [COLOR=black]succes[/COLOR]sful TERMINAL will output
> ns1.YOURDOMAINENAMEHERE.COMType in the following command in TERMINAL to update the apt-get packages repositories:
    ```
apt-get update
```Wait. This might take up to 5 minutes. If [COLOR=black]succes[/COLOR]sful TERMINAL output:
>      Reading package lists... Done Type in the following command in TERMINAL to update to the latest packages:
This will update your remote Ubuntu Server to the latest version. Currently 8.04.2 
        ```
apt-get upgrade
```TERMINAL will ask 'Do you want to continue [Y/n]?'.
Type in Y then press RETURN key.
Wait. This might take up to 15 minutes. If [COLOR=black]succes[/COLOR]sful TERMINAL output a lot of lines.

If TERMINAL returns the following error:
>          LANGUAGE = (unset),
LC_ALL = (unset),Then you must install another package. To do so type in the following command then press RETURN.
        ```
apt-get install language-pack-en
```TERMINAL will ask 'Do you want to continue [Y/n]?'.
Type in Y then press RETURN key.
If [COLOR=black]succes[/COLOR]sful TERMINAL will return lot of lines.

Type in the following command in TERMINAL to install 'screen' and 'wget'. Those will be use by the coming Virtualmin installation script 'install.sh'
        ```
apt-get install screen wget
```We are now going to download the free open source Virtualmin installation script. This script is going to do all the hard work for you.
Type in the following command in TERMINAL to download the installation script to your remote Ubuntu Server:
    ```
wget [http://software.virtualmin.com/gpl/scripts/install.sh](http://software.virtualmin.com/gpl/scripts/install.sh)
```Type in the following command in TERMINAL to set the permissions on the installation file:
```
chmod +x install.sh
```We are now going to make sure that there’s at least 2GB (2048MB) SWAP disk available for Virtualmin installation script (install.sh) otherwise the installer will run out of memory. You can reduce the SWAP to 512MB after installation. 

Type in the following command in TERMINAL to know the current size of your SWAP disk:
    ```
df -m
```TERMINAL will return the current size of you SWAP disk. Size is in MB. The number you're looking for in the first column titled '1M-blocks' and the first line. In my case my number is 2206. So I'm good to go to the next step.

Type in the following command in TERMINAL to install Virtualmin & Webmin & Usermin from within SCREEN:
    ```
sudo ./install.sh
```Terminal will ask 'Continue? (y/n)'.
    Type in y and press RETURN key.

Wait. The spinning bar means that the installation is in progress. It can take up to 30 minutes. Wait.

When the installation script is done the spinning bar will disappear.

Important note: Once Virtualmin is installed, you never need to run this script again.

Reboot your remote Ubuntu Server to make all the changes active.

Go to: [https://123.123.123.123:10000/](https://123.123.123.123:10000/)

    Note 1: You must replace above 123.123.123.123 by your remote Ubuntu Server IP address.
    Note 2: The link starts with https:// not http:// The 's' means secure connection.

If the script installation is [COLOR=black]succes[/COLOR]sful you should see Webmin control panel.

Note: If your internet browser is Firefox version 3 it will display the following message “Secure Connection Failed”. That's normal. You must let Firefox know that your remote Ubuntu Server is safe. To do so: 
Click on ”Or you can add an exception…” link.
Click on ADD EXCEPTION link.
Click on GET CERTIFICATE button.
Click on CONFIRM SECURITY EXCEPTION button.

If working you'll see your Webmin log in page.
Type in your username & password. Your username & password are the same as your remote Ubuntu Server. Your username is usually 'root' unless you changed it. 

The first Webmin page is title ”Post-Installation Wizard”
The following message is display under the title ”This post-installation wizard allows you to configure Virtualmin optimally for your system. You can make selections depending on whether you want to host websites, email or databases, and based on your system's memory and CPU power.To continue, click the Next button below. To skip it and use the default settings, click Cancel.”

Click on NEXT button.
Set your preference to match your needs. You can change your settings later.

In my case I have a limited amount of RAM available so to use less RAM my settings are as follow:
        Preload Virtualmin libraries? NO
        Run email domain lookup server? NO
        Run ClamAV server scanner? NO
        Run SpamAssassin server filter? NO
        Run MySQL database server? YES because I'll add Drupal later.
        Run PostgreSQL database server? NO because I use MySQL instead.
        Set MySQL password? For security reason you should choose a different password than your remote Ubuntu Server. 6 to 16 alphanumeric and characters max. No symbol allowed.

After completing the WISARD Webmin will return the following message under the title at the top of your screen: ”All done”
Click on NEXT button.

A yellow box will be display at the top of Webmin interface.
Click on RE-CHECK AND REFRESH CONFIGURATION button.

If [COLOR=black]succes[/COLOR]sful the following message will display close by the bottom:
> .. your system is ready for use by Virtualmin.We are now going to refresh the Webmin modules display.
Click on WEBMIN link located on the top left side of your screen.
Click on REFRESH MODULES link.  

If [COLOR=black]succes[/COLOR]sful Webmin returns a message like > “.. found 68 with installed applications, 43 not installed.”Click on VIRTUALMIN link located on the top left side of your screen.
Click on SYSTEM INFORMATION link located on the left side of your screen.
Find the line REAL MEMORY. This line provides information on your remote Ubuntu Server memory.
The first number is your total memory. And the second number is your used memory. In my case the used memory is around 150MB.

Important note 1: Once Virtualmin is installed, you never need to run this script again. This is a installation script NOT an updates script.

Important note 2: For now on Virtualmin, Webmin & Usermine upgrades and updates should be done within Virtualmin itself. Not TERMINAL.

That's it you're done. You have [COLOR=black]succes[/COLOR]sfully installed Virtualmin, Webmin & Usermine on a remote Ubuntu Server.

Enjoy

Onopoc

Source: [http://www.virtualmin.com/documentation/installation/automated](http://www.virtualmin.com/documentation/installation/automated)

---

### Post by dmizer on 2009-06-28
I'm always concerned about howtos that advocate webmin.

I think this tutorial also makes lots of mistakes like changing from DHCP to Static IP without explaining why, suggesting that root access (over ssh) is required, etc.

---

