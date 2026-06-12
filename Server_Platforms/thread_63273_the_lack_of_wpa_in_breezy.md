---
title: "the lack of wpa in breezy"
date: 2005-09-07
forum: Server Platforms
---

### Post by water on 2005-09-07
I'm aware of the various how-to's that provide information for setting up wpa in Ubuntu. However I feel that the lack of wpa support in a vanilla Breezy install represents a mayor security problem for all categories of users.

As far as I've been able to find out from ubuntu.com there are no plans to bring the wifi security level of Breezy past the far to in-secure wep standard.

Does anybody know if there are any serious plans to implement proper wpa support into Ubuntu post-breezy or if there are any other projects in the works that might help adress the seriuos issue?

:water

---

### Post by seiflotfy on 2005-09-14
yeha i was wondering that too

---

### Post by water on 2005-09-16
I'm thinking that the silence on in this has two reasons ;

[list]
[*]it's been discussed several times in several threads
[*]nobody knows ;)
[/list]For me this lack of wps is a showstopper when it comes to deplying Ubuntu as the Liunx distribution of choice in a pilot project in out organization.

I really do belive we could do with a serious push in this area, and a discussion focused on the security implications of this lack of wpa support.

...running of to check out the bounty system...  ;)

:water

---

### Post by UbuWu on 2005-09-16
Do other linux distro's have wpa support? Or is it a general problem with linux?

---

### Post by water on 2005-09-23
I'm not sure of how wpa support is available (or not) in other distros.

However I'm pretty unpatient as this is holding me back for launching a Ubuntu on the desktop pilot project.

:water

---

### Post by John.Michael.Kane on 2005-09-23
[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=WPA)
[http://www.ubuntuforums.org/showthread.php?t=61516&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=61516&highlight=WPA)
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=WPA)
[http://www.ubuntuforums.org/showthread.php?t=38942&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=38942&highlight=WPA)
[http://www.ubuntuforums.org/showthread.php?t=31926&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=31926&highlight=WPA)
[http://www.ubuntuforums.org/showthread.php?t=31418&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=31418&highlight=WPA)
[http://www.ubuntuforums.org/showthread.php?t=25398&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=25398&highlight=WPA)

hope this helps...

---

### Post by jcostom on 2005-09-23
[QUOTE=UbuWu]Do other linux distro's have wpa support? Or is it a general problem with linux?[/QUOTE]

Most current distro's are shipping with wpa_supplicant, however, the number that offer reasonable configuration of it is small.

The only one I've been successful at using without first tearing out half of my hair has been SuSE 9.3.

Using WPA2 with PSK here successfully under SuSE 9.3.  If Ubuntu had solid WPA/WPA2 integration available, I'd use it in a second.  I prefer Ubuntu over SuSE, but if networking doesn't go, the point is sort of moot.

---

### Post by alper_tr on 2005-10-20
I read the forums, internet etc.. and failed to get wpa-psk work on breezy... Imaybe its my fault, however seems like most people are having that problem as well. Wish a software come up from gnome to resolve that...
my desk is far from the internet cable.. and i can only get it via wireless.. :(

---

### Post by SubZero_AK on 2005-10-20
It really isn't that hard to get WPA working in Linux.  I say in Linux  and not specifically Ubuntu because it is mostly universal when done from the command line.  The whole process for me was less than 5 minutes after I installed Breezy because it was the first thing I did.  I found the information with a simple search of these very forums.  This was for my laptop with the Centrino wireless card IPW2200.  I also got my desktop using Debian and ndiswrapper using the same technique with a slightly different conf file.

First, I did:
sudo apt-get install wpasupplicant

Then I did:
sudo gedit /etc/wpa_supplicant.conf:

Then entered my configuration, similar to this:

	ctrl_interface=/var/run/wpa_supplicant

	network={
       		ssid="your_network_name"
       		scan_ssid=1
       		proto=WPA
       		key_mgmt=WPA-PSK
       		psk="your_secret_key"
		}

Next:
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -d


All of this I obtained from the following thread:
[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=WPA](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=WPA)

Mark

---

### Post by Azrael on 2005-10-21
[quote=SubZero_AK]It really isn't that hard to get WPA working in Linux.[/quote] Your anecdotal evidence is worth little when looking at the large picture. You are lucky to have an out-of-the-box supported IPW2200. Many wireless cards require a high degree of customization to get working at all. Finding the right driver/module/kernel/hotplug/encryption configuration can unfortunately still be disgruntling even for the more moderately computer savvy user. I know much of that is caused by undocumented hardware specifications, but I feel Linux would nevertheless benefit from a more unified framework when dealing with wireless networking -- including WPA support.

---

### Post by marcosscriven on 2005-10-21
Hi

I wouldn't say SubZero_AK's posting is worth little - it helped me get wpa-psk working on my Thinkpad immediately! However, it did sound a teeny bit aloof ;) 

I do have a few more questions though:

1) When I reboot - the computer hangs for a good few minutes at the 'bringing up network' part. Then says 'fail' before moving on. When I get to the desktop, sure enough, no wireless. I rerun the wpa_supplicant command SubZero_AK mentioned - and fine again. How do I automate this, so it starts up and says 'ok' on bootup? What is that particular wireless network is not available?

2) How do I add other networks in the future? Do I have to add another entry to the .conf everytime I go to another wpa-psk secured network? Is there no GUI tool?

It does seem really quite hard to setup - unless some has done it, and spells it out exactly. 

Marcos

---

### Post by SubZero_AK on 2005-10-21
[QUOTE=Azrael]Your anecdotal evidence is worth little when looking at the large picture. You are lucky to have an out-of-the-box supported IPW2200. Many wireless cards require a high degree of customization to get working at all. Finding the right driver/module/kernel/hotplug/encryption configuration can unfortunately still be disgruntling even for the more moderately computer savvy user. I know much of that is caused by undocumented hardware specifications, but I feel Linux would nevertheless benefit from a more unified framework when dealing with wireless networking -- including WPA support.[/QUOTE]


So my ancedotal evidence is worth little, then your reply is worth even less.  If you even read my entire post you would have seen that I have WPA up on more than just my "supported" IPW2200.  I have used NDISWRAPPER for another machine with WPA.  In addition to that I have also setup...my wife's Orinoco...my Senao with prism 2.5 chipset using HostAP drivers...A friend's Dell with Broadcom also using NDISWRAPPER.  The steps are all pretty much the same.  

As a matter of fact, if you visited the link that I added in my post you would have seen that IPW2200 wasn't always supported.

The purpose of my post was to demonstrate some of the basics involved in adding WPA to your wireless connection

Bottom Line:

WPA support exists in Linux.  It's not that difficult.  There is lots of help available if you have problems.

-Mark

---

### Post by SubZero_AK on 2005-10-21
[QUOTE=marcosscriven]Hi

I wouldn't say SubZero_AK's posting is worth little - it helped me get wpa-psk working on my Thinkpad immediately! However, it did sound a teeny bit aloof ;) 

I do have a few more questions though:

1) When I reboot - the computer hangs for a good few minutes at the 'bringing up network' part. Then says 'fail' before moving on. When I get to the desktop, sure enough, no wireless. I rerun the wpa_supplicant command SubZero_AK mentioned - and fine again. How do I automate this, so it starts up and says 'ok' on bootup? What is that particular wireless network is not available?

2) How do I add other networks in the future? Do I have to add another entry to the .conf everytime I go to another wpa-psk secured network? Is there no GUI tool?

It does seem really quite hard to setup - unless some has done it, and spells it out exactly. 

Marcos[/QUOTE]

Marcos thanks for the comment :P  Please read the remainder of the thread that I linked in my previous post, it outlines how to automate the WPA supplicant.

Regarding 1):

edit your /etc/network/interfaces

Look for :
# The primary network interface

    What I did was this:

#iface eth0 inet dhcp           <----I commented this out
auto eth1                           <----I added this
iface eth1 inet dhcp             <----this
wireless-essid MywirelessAP   <----and this

*Note*  there is no entry for an encryption key
That is because the encryption is handled by the wpasupplicant.

Regarding 2):
Add the other networks as a new entry to your /etc/wpa_supplicant.conf like this:

network={
        ssid="Subzero"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ChooseaverycomplicatedphrasesoIdon'tbreakin"
}


-Mark

---

### Post by marcosscriven on 2005-10-22
Thanks again Mark

unfortunately, that didn't work :( Here's my interfaces files:
-----
auto lo
iface lo inet loopback

mapping hotplug
            script grep
            map eth0

iface eth1 inet dhcp
wireless-essid MYWIRELESSID

auth eth1
----

When I reboot - it now doesn't pause so long, and *does* say ok. BUT - no wireless when I log in :( 

The only way I can get it to work is by typing your command:

sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -d

Then everything is hunky dory. I suppose I could make that a one line .sh script, and put it in startup, but that seems a bit hacky?

Thanks again for your help

Marcos

---

### Post by SubZero_AK on 2005-10-22
You're right,
     It is hacky, and it would be nice for Ubuntu to place a more user friendly way of getting it to work in their distro.  Here is the script which I blatantly ripped off from luca_linux, another member of these forums:

Here's the script: Create it as /etc/init.d/wifi_wpa.sh
Code:

#! /bin/sh 
# wifi: wpa_supplicant 
init echo " * [Wifi]: Enabling WPA supplicant..." 
if [ -x /usr/sbin/wpa_supplicant ]; then[INDENT]/usr/sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w [/INDENT]
fi 
exit 0

Change the script's permissions to allow it to be executed:
Code:

sudo chmod +x /etc/init.d/wifi_wpa.sh

And create a symlink to define the relative service:
Code:

sudo ln -s /etc/init.d/wifi_wpa.sh /etc/rcS.d/S40netwifiwpa

After that it's automatic...:rolleyes:

-Mark

---

### Post by janne5011 on 2005-10-29
my solution as a new user (one week), is to use something like this:
[http://www.dlink.com/products/?pid=241](http://www.dlink.com/products/?pid=241)
I know its possible apply wp-psk but for me its to much trouble with several pc:s ..its to much editing textfiles and what happend if one do a upgrade.. old settings away and again the damned textfileediting ...:???: .
Especially for laptops users this is good and one can be sure thoose products always work,  and,they  cost only little more than a wireless card.(most motherboards nowadays have integrated networcards)
this solution suits my situation ..see it as a alternative 
also remeber if you have some old AP not in use, they often can be configured as a client.

sorry my English is not English hope it can be understood:KS :KS :KS 
thanks

---

