---
title: "Script to connnect automatically to a US VPN (OpenVPN)"
date: 2015-12-27
forum: Tutorials
---

### Post by matbonucci on 2015-12-27
Hi I made this script for myself to connect to Spotify because is not available in my country and i want to share it. It just creates a hidden folder in home folder with a few text files.
You must have installed openvpn if not "sudo apt-get install openvpn"
```

#! /bin/sh
mkdir $HOME/.vpnbook #Creates the directory for all this
wget -r http://www.vpnbook.com/free-openvpn-account/VPNBook.com-OpenVPN-US1.zip -P $HOME/.vpnbook #Download the ovpn files
wget --recursive --page-requisites --html-extension --convert-links --restrict-file-names=windows --domains website.org --no-parent http://www.vpnbook.com/freevpn -P $HOME/.vpnbook #Download the html to retreive the public password from OpenVPN
unzip -o -d $HOME/.vpnbook $HOME/.vpnbook/VPNBook.com-OpenVPN-US1.zip #Unzip
var=`grep "Password" $HOME/.vpnbook/www.vpnbook.com/freevpn.html` # Retrieve the line with the password from freevpn.html and save it in the var variable, but it gets two lines so let's trim it
var=`echo "$var" | sed -e "1d"` #Trim the variable to one line
var=`echo "$var" | cut -b 1-26 --complement` && var=`echo "$var" | cut -b 9-25 --complement` #Trim the html parameters and only remains the password
echo -e "vpnbook\n$var" >> $HOME/.vpnbook/loginUTF8.conf #Creates the login.conf with the username and the password from the freevpn.html file
iconv -f UTF-8 -t US-ASCII $HOME/.vpnbook/loginUTF8.conf > $HOME/.vpnbook/login.conf #Convert the login.conf file to Windows Unicode to be valid for the openvpn command
sed "s|auth-user-pass|auth-user-pass $HOME/.vpnbook/login.conf|g" $HOME/.vpnbook/vpnbook-us1-tcp443.ovpn > $HOME/.vpnbook/vpnbook-us1-tcp443_new.ovpn #Now the new ovpn file knows where is the login.conf with the username and the password to use. WAS A NIGHTMARE finding out how to use sed with "/" for the directories
gksu -- openvpn --config $HOME/.vpnbook/vpnbook-us1-tcp443_new.ovpn & #Finally connecting. The login.conf must be Windows Unicode format and the ovpn file does not recognize the $HOME variable but the sed command do the job in the upper line
sleep 40 #Wait for the VPN service to connect
notify-send 'Connected to the USA VPN'

```

And this one is to disconnect from the VPN or just use "gksu killall openvpn"
```

#! /bin/sh
gksu killall openvpn
rm $HOME/.vpnbook/login.conf
rm $HOME/.vpnbook/loginUTF8.conf
#Those files are removed because if the script runs again it will not use the old password

```

Just copy those lines and save it to a text file and rename it to *yourtitle*.sh and double click on in it to execute them ;)
Or open the terminal where the .sh is and type "bash *yourtitle*.sh"

---

### Post by dave205 on 2015-12-27
interesting that this uses a free vpn service as the provider and openvpn to run the actual vpn.   great job!

---

### Post by yetimon_64 on 2015-12-30
Be aware your script does not do any checking for the presence of openvpn even being installed and appears to be working even if it isn't here. I was notified I was "Connected to the USA VPN" even without openvpn being installed here ...

> ```
yetiman:~ $ policy openvpn
openvpn:
  Installed: (none)
  Candidate: 2.3.2-7ubuntu3.1
  Version table:
     2.3.2-7ubuntu3.1 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     2.3.2-7ubuntu3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
```
Note, I am using a bash alias, "policy", above for the command "apt-cache policy".

The line "gksu -- openvpn --config $HOME/.vpnbook/vpnbook-us1-tcp443_new.ovpn &" should probably not be using the command openvpn as a switch to the gksu command but more starting like "gksu openvpn --config ...", gksu is not the main command, openvpn is with gksu for privilege escalation. 

Even with this set up it appears to be working; that is there is no check for a valid vpn connection just a notification of connection issued after a sleep command.

Nice start but needs quite a bit of reviewing for safety in my opinion as it is for vpn usage. Interesting concept if fleshed out a bit more code wise.

Also once the vpn is set up how do you use it to connect to spotify etc ? (or for any other process/browser to use it; this seems like only the first basic steps in the full process you mention usage wise). 

Kind regards, yetimon_64

---

### Post by matbonucci on 2015-12-31
A

---

### Post by matbonucci on 2015-12-31
Hi. You’re right, i forgot i installed openvpn time ago and i assumed it was already installed, i will include the installation on the script.
I used "gksu --" because gksu had problems with openvpn parameters, so it is with others commands with parameters. That's why is necessary "gksu --" to omit later problems with parameters.
Yes this only shows a notification after the openvpn command. To be honest i don't know how to use openvpn connection status to the script and to show if it was connected successfully or not.

And for spotify i just have to open app every two weeks with a US connection or it would close my session because i'm not in the US. I found tedious looking for the vpnbook password and doing the connection every week, i always forgot so that was the main use for the script. But after this i can use the app normally without a VPN for two weeks. So no other process after i run the script for me, just open Spotify and disconnect from the VPN.

I edited my script that after the VPN connection it finds if Spotify is running (I'm listening to music) or not. If the app is running it waits 3 minutes with the VPN connection open then close the VPN connection so the app will know i was conected the the US, if is not running after the VPN connection it will open Spotify for 3 minutes then close the app and close the VPN connection. I run it every Sunday

---

