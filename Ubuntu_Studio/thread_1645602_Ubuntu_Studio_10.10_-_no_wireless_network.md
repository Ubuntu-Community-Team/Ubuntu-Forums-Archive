---
title: "Ubuntu Studio 10.10 - no wireless network"
date: 2010-12-14
forum: Ubuntu Studio
---

### Post by hueygunner on 2010-12-14
Installed Studio 10.10 three times and I cannot get wireless networking to work at all.  I'm a newbie as far as Ubuntu is concerned.

---

### Post by cipherboy_loc on 2010-12-14
Open up the terminal (Applications -> Accessories -> Terminal) and type in: 

```

lspci | grep -i 'net'

```


This will tell us whether or not you need a special driver to make it work.



Cipherboy

---

### Post by hueygunner on 2010-12-14
> **cipherboy_loc said:**
> Open up the terminal (Applications -> Accessories -> Terminal) and type in: 

```

lspci | grep -i 'net'

```


This will tell us whether or not you need a special driver to make it work.



Cipherboy
09:00.0 Network controller: Atheros Communications Inc.  AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by hueygunner on 2010-12-14
> **cipherboy_loc said:**
> Open up the terminal (Applications -> Accessories -> Terminal) and type in: 

```

lspci | grep -i 'net'

```


This will tell us whether or not you need a special driver to make it work.



Cipherboy
Everything I typed in my earlier Quick Reply disappeared.  I've got information on a wireless and a wired network adapter so I assume they're installed properly.  I'm using my EEE PC netbook to read this forum.  Ubuntu Studio is installed on my HP dv7 laptop.

---

### Post by hueygunner on 2010-12-14
I'm tired.  I've been on this problem for more than 5 hours without any success.  I can't believe such an important feature/program is intentionally left out of any modern OS.  We're in the Internet Age: An operating system without a network wizard is a dinosaur.  :confused:

---

### Post by ajack38 on 2010-12-15
Go to synaptic and search for "wicd". It's a simple network manager that kinda works like the vista network manager but it's easier to understand.

---

### Post by hueygunner on 2010-12-15
I tried to run synaptic but it wouldn't start.  I "googled" that phrase and I found the answer.  Now, I've started synaptic with the terminal command "gksudo synaptic" and I've typed in "wicd" in three search boxes.  I'm in "Select directory" in Synaptic Package Manager and typed in "wicd" in the search box.  I've clicked "Open."  What happens next?  ):P

---

### Post by hueygunner on 2010-12-16
Thanks, but I don't think WICD is the answer for me.  I understand it will knock out Network Manager which is installed.  I'm not having any luck with NM but I don't want to uninstall something that is working although I don't know how to configure wireless networking with it.  Being a newbie, I'm afraid to disable any installed programs.  Better to be cautious than sorry.  :-\"

---

### Post by hueygunner on 2010-12-16
Problem was solved by un-installing Ubuntu Studio 10.10 and installing Ubuntu 10.10 then upgrading it to Ubuntu Studio 10.10.

---

### Post by nickkemming on 2010-12-21
really???? you're calling this a solution? it's like buying a new car when your headlight doesn't work...

can someone please post a workable solution that doesn't require reinstalling ubuntu?
i am very disappointed that such a basic feature doesn't work out of the box...

---

### Post by Totalchaos on 2010-12-21
> **nickkemming said:**
> really???? you're calling this a solution? it's like buying a new car when your headlight doesn't work...

can someone please post a workable solution that doesn't require reinstalling ubuntu?
i am very disappointed that such a basic feature doesn't work out of the box...

There is Two basic principals that you must concern if you want an answer to your question:

1.If it works on ubuntu it will work on ubuntustudio and vise-versa, because of the same origin of the two OS's
2.Audio-production and networking doesn't like each other very much. so ubuntustudio finds a simpler solution by not including this option in their OS. The explanation is that in audio production your computer's OS tries to use less processes as possible to achieve
realtime priority of them. For instance in the servers is the opposite the computer tries to run as many processes as possible.    That's why the audio-production superusers tries to get rid of any unnecessary processes like compiz, pulseaudio, openGL, cairo-docks etc,etc, because the goal is lowlatency audio with less x-runs  

If you have a notebook or a netbook i can recommend you to try PyreDyne . It's a very nice multimedia orientated OS based on Karmic created especially for notebooks and netbooks and it can be started via usb/liveCD. 

PS: Did you try 'apt-get install wicd'

---

### Post by grahammechanical on 2010-12-23
I solved this a different way. I could not install Network Manager as I did not have even an ethernet connection working in Ubuntu Studio. In my standard Ubuntu partition I have both wired and wireless working.

This is what I worked out for Ubuntu Studio;

1) Something is needed to indicate that an Internet of networking connection has been made. 

Right click the top panel and select Add to Panel. In the list presented by the dialog box select Network Monitor [Monitor network activity]. Click Add.

This action will put an icon of two connected monitors (screens) that will flash when there is network activity. It is reassuring to have this.

2) Setting up connections. Click on the Ubuntu Studio icon on the left of the top panel. Go to System>Administration>Network.

Do not go to System>Preferences>Network. It is the wrong type of network.

In the dialog box that appears select the Connections tab. Click the shield icon at the bottom and in the middle of the dialog box. It has "Click to make changes" alongside it.

Enter your login password. A list of available connections will appear. Select either Wireless Connection, Wired connection (eth1) or Wired connection (eth0) and click the Properties button.

For a Wireless connection put a tick mark against the box "Enable this connection". 

Make sure that the network name (ESSID) is the correct one.

Set the password type WPA Personal.

Enter the Network password. This is the wireless key or WPA-PSK key.

Set the configuration to Automatic configuration (DCHP) if that is the correct setting.

Enter if necessary the IP address, Subnet mask, Gateway address.

Click OK.

Click the make changes shield to prevent any further changes.

Click close and then reboot. Cross your fingers. You may need to shutdown and boot more than once. It is strange, I know but there you are.


Some other information: Left or right click the Network Monitor icon to see the Connection Properties of wlan0

A dialog will appear that will give the connection name, its status, an activity report (packets and Kilo bits received and sent) and signal strength. There is also a button to Configure the connection. Every time I click this button I get a Interface does not exist message even though there is an active connection.

If all else fails you can also type in a terminal  sudo ifconfig wlan0 up and sudo ifup -v eth0 or sudo ifup -v eth1

regards.

---

### Post by Muzzab on 2011-01-06
I don't know man, I tried all this and I've got no ethernet, I  apparently have a wireless signal but still no internet working, I tried  the ifconfig wlan0 up commands you suggested and stuff but I'm still  getting nothing. Maybe I should just give up and don't worry about  ubuntpoo studio and go back to windows. Wasting my time here. If anyone  has any better ideas than that, let me know! I hate windows but at least  it works.

---

### Post by jorgealfonso on 2011-01-13
Same issue. Got solved installing wicd, downloading the packages from another computer with working internet.

I also needed to download and install python-urwid first, which is a dependency of wicd.

Thanks :)

---

### Post by jorgealfonso on 2011-01-13
By the way, saw on this thread that audio production doesn't like networking... fine, but we have to recognize that in our days Internet is a BASIC need.

Would somebody have a solution to conciliate audio production and networking? (ex: prioritizing audio somehow?)

---

### Post by nigel_bowers on 2011-01-15
Go to [https://help.ubuntu.com/community/UbuntuStudioNetworkSetup](https://help.ubuntu.com/community/UbuntuStudioNetworkSetup)   The reason wireless is left out (and the way to enable it) is detailed here.

---

### Post by maen on 2011-01-15
I found that by doing the install with a wired internet connection (ie plugged into ethernet port on my wireless router) nm-applet etc seemed to behave much more like normal. If that's an option for you, maybe worth a try.

---

### Post by Wejdan on 2011-01-29
> **ajack38 said:**
> Go to synaptic and search for "wicd". It's a simple network manager that kinda works like the vista network manager but it's easier to understand.

Im having the same issue
I tried this but no packages were found..
also, tried installing network manager from installation CD but received : > Error: dependency is not satisfiable

any help plz:(

---

### Post by Wejdan on 2011-01-29
> **nigel_bowers said:**
> Go to [https://help.ubuntu.com/community/UbuntuStudioNetworkSetup](https://help.ubuntu.com/community/UbuntuStudioNetworkSetup)   The reason wireless is left out (and the way to enable it) is detailed here.

not working, some packages are installed some are not "error: dependency is not satisfiable" ! :S

---

### Post by Wejdan on 2011-01-29
> **grahammechanical said:**
> I solved this a different way. I could not install Network Manager as I did not have even an ethernet connection working in Ubuntu Studio. In my standard Ubuntu partition I have both wired and wireless working.

This is what I worked out for Ubuntu Studio;


Worked just fine :D
thank you :KS

---

