---
title: "Password protect wireless card"
date: 2009-01-22
forum: Security
---

### Post by toddr on 2009-01-22
Ok. This is what I want to do:
1) Disable the wireless card to all non-administrative users
2) Password protect wireless card
3) Have a menu entry and or task bar button to turn on and off the wireless 
   card with a password prompt box.

The computer in question is a Dell Inspiron 1505n with the Dell version of Hardy Herron 8.04.1 installed

So, is this possible? I've been using Linux for about two years now but am still kind of a noob.

Any ideas would be much appreciated. Thanks

---

### Post by hyper_ch on 2009-01-22
wouldn't it just be simplre to use WPA2 on the wireless network and don't store the passwort do it in your network manager?

---

### Post by toddr on 2009-01-22
I do use wpa encryption. How do I prevent network manager from automatically connecting to my network? In Fiesty 7.04 network manager would always prompt for the password for non-administrator accounts. For some reason Hardy automatically connects.

---

### Post by hyper_ch on 2009-01-22
there should be a setting where you should be able to deactivate auto-connection... but I haven't use the official network manager for a long time.

---

### Post by tubbygweilo on 2009-01-22
I think you should be able to set user access to wireless and networks  via 
```
System > Administration > Users and Groups > Properties > User Privileges
```
I know you can in 8.10 but in 8.04.01 I have no idea.

---

### Post by toddr on 2009-01-22
Yea, I can completely block the user from the internet all together with user privileges, but, I just want to block access until the password is punched in.

---

### Post by toddr on 2009-02-05
..........bump...............

---

### Post by toddr on 2009-02-05
Perhaps I'm looking at this wrong. Is there a way to cause the password manager to expire the password at the end of every session or at logout?

---

### Post by tturrisi on 2009-02-07
Why not just dump the buggy network-manager and use a script to logon to wifi networks.  You can create a desktop or panel icon that starts the script.  Use sudo instead of gksudo.

---

### Post by toddr on 2009-02-07
Wow, that would be great! Forgive the nooby question, but, how would I go about it? I think I can handle removing network manager. Do you have a script I could use? Thanks for the reply!

---

### Post by tturrisi on 2009-02-08
wlassist.sh

```
#!/bin/bash

################################################################
## PROJECT #####################################################
################################################################
## Date    : 09/02/2007                                       ##
## Program : wlassist                                         ##
## Author  : Mark A. LaDoux                                   ##
## Website : http://www.haktstudios.com                       ##
## E-Mail  : t0nedef@haktstudios.com                          ##
################################################################
## DESCRIPTION #################################################
################################################################
## Console application to simplify the maintainence of        **
## wireless network settings. It stores configurations and    ##
## recalls them when requested. It is capable of handling     ##
## unencrypted, WEP, and WPA encrypted networks.              ##
################################################################
## DEPENDANCIES ################################################
################################################################
## Wireless capable device                                    ##
## bash 2.x or better                                         ##
## linux wireless utils (for configuring wireless card)       ##
## wpa_supplicant (for accessing wpa networks)                ##
## permissions to modify network settings                     ##
################################################################
## COPYRIGHT ###################################################
################################################################
## ©2007 Hakt Studios. http://www.haktstudios.com             ##
##                                                            ##
## This program is free software; you can redistribute it     ##
## and/or modify it under the terms of the GNU General        ##
## Public License as published by the Free Software           ##
## Foundation; either version 3 of the License, or (at your   ##
## option) any later version.                                 ##
##                                                            ##
## This program is distributed in the hope that it will be    ##
## useful, but WITHOUT ANY WARRANTY; without even the implied ##
## warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR    ##
## PURPOSE.  See the GNU General Public License for more      ##
## details.                                                   ##
##                                                            ##
## You should have received a copy of the GNU General Public  ##
## License along with this program.  If not, see              ##
## <http://www.gnu.org/licenses/>.                            ##
################################################################

## Ok to start we are going to define a couple of things      ##
## please adjust thes variables to match your hardware        ##
DRIVER=wext   ## This is the driver to use for wpa_supplicant ##
IFACE=ath0    ## this is the network interface to use         ##

## DO NOT EDIT ANYTHING BELOW THIS POINT                      ##

RUID=0 # root uid
WDIR=/etc/wlassist # where settings are stored

E_NR=65 # not root
E_IO=66 # invalid option
E_NF=67 # Not Found
E_UC=68 # User Canceled

function CONTINUE(){
echo "Would you like to continue? (Y/n)"
read YESNO
if [ "$YESNO" == "N" ] || [ "$YESNO" == "n" ]
then
  echo "Terminating program per user request..."
  exit "$E_UC"
fi
}

function ENCRYPT(){
echo "What encryption does $ESSID use?"
echo ""
echo "1) none"
echo "2) WEP"
echo "3) WPA"
CFILE=$WFILE.conf
read CRYPT
case "$CRYPT" in

  "1" )
  echo "You have chosen to not use encryption..."
  CONTINUE
  echo "Saving settings...."
  echo "#!/bin/bash" >> "$WFILE"
  echo "iwconfig $IFACE essid $ESSID" >> "$WFILE"
  echo "dhclient3 $IFACE" >> "$WFILE"
  chmod +x "$WFILE"
  echo "Initializing connection"
  "$WFILE"
  exit 0
  ;;

  "2" )
  echo "You have chosen to use WEP..."
  CONTINUE
  echo "Ok, now I would like to collect some info from you."
  echo "What is your WEP Key?"
  read KEY
  echo "Please double check the key for errors before continuing."
  echo "$KEY"
  CONTINUE
  echo "Saving settings..."
  echo "#!/bin/bash" >> "$WFILE"
  echo "iwconfig $IFACE essid $ESSID key $KEY" >> "$WFILE"
  echo "dhclient3 $IFACE" >> "$WFILE"
  chmod +x $WFILE
  echo "Initializing connection"
  "$WFILE"
  exit 0
  ;;

  "3")
  echo "You have chosen to use WPA..."
  CONTINUE
  echo "Okay, now I would like to collect some info from you"
  echo "What is your WPA passphrase?"
  read PSK
  echo "Please double check your passphrase for errors before continuing."
  echo "$PSK"
  CONTINUE
  echo "Saving settings..."
  ## begin conf file
  echo "network={" >> "$CFILE"
  echo "  ssid=\"$ESSID\"" >> "$CFILE"
  echo "  psk=\"$PSK\"" >> "$CFILE"
  echo "}" >> "$CFILE"
  ## begin script file
  echo "#!/bin/bash" >> $WFILE
  echo "wpa_supplicant -D$DRIVER -i$IFACE -c$CFILE &" >> "$WFILE"
  echo "dhclient3 $IFACE" >> "$WFILE"
  chmod +x $WFILE
  echo "Initializing connection"
  "$WFILE"
  exit 0
  ;;
  * )
  echo "Invalid option, exiting program..."
  exit "$E_IO"
  ;;
esac

}

## Program Begins Here ##

if [ "$RUID" != "$UID" ]
then
  echo "I'm sorry, but you don't seem to have proper permission"
  echo "to perform this action"
  exit "$E_NR"
fi

if [ ! -e "$WDIR" ]
then
  mkdir "$WDIR"
fi

echo "Would you like to scan available networks? (y|N)"
read NOYES

if [ "$NOYES" == "Y" ] || [ "$NOYES" == "y" ]
then
  iwlist "$IFACE" scan # | more
fi

echo "Which network would you like to connect to today?"
read ESSID
echo "You chose $ESSID..."
CONTINUE
WFILE=$WDIR/$ESSID

if [ ! -e "$WFILE" ]
then
  echo "No configuration for $ESSID currently exists!"
  ENCRYPT
fi

$WFILE

exit 0
```

---

### Post by toddr on 2009-02-13
That looks good, but I don't think it would serve my purposes. I would like a gui front end with a panel button. I've been thinking about using Zenity to have a password box pop up when pressed to access network manager or even Wicd. My problem with that is I have no idea how to write a shell script to do such a thing.

---

### Post by t0nedef on 2009-08-07
Wow.... That's such an old version of my script, and would be buggy on ubuntu systems, * I've made fixes and since updated it to version 1.3

[-=DOWNLOAD=-](http://sites.google.com/site/kouenin/Home/wlassist-1.3.tbz2?attredirects=0)


anyway, sorry it won't help with your issue, it may help with someone else... who knows. I think i have a 1.4 version sitting around, but meh.

---

