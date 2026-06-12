---
title: "Fails to start Firestarter ... can't run in Gnome!"
date: 2004-11-22
forum: Server Platforms
---

### Post by svarreby on 2004-11-22
I receive this message when I try to run Firestarter (from Applications -> Internet -> Firestarter Firewall Tool):

Failed to run /usr/sbin/firestarter as user root:
Wrong password.

..Eehhhh, am I missing some important info here ... :-)

---

### Post by jdong on 2004-11-22
use **gksudo firestarter**. Firestarter still is unchanged/unpatched... it assumes the existence of a root account.

---

### Post by Burgundavia on 2004-11-24
To add the to the previous message, right click on the icon in the menu for firestarter and change it to gksudo from gksu. 

Hopefully that is more clear, but you might have already figured that out already

Corey

---

### Post by Sniffer on 2004-11-26
Thanks with the exact same problem.

One question??

Can i uninstall iptables now or better how can i disable iptables if i can't uninstall it (if it's the case).

Thks.

---

### Post by ubuntu_demon on 2004-11-26
[QUOTE=Sniffer]Thanks with the exact same problem.

One question??

Can i uninstall iptables now or better how can i disable iptables if i can't uninstall it (if it's the case).

Thks.[/QUOTE]
 No you can't uninstall iptables. Firestarter uses iptables. 

Why would you want to uninstall iptables ? There's nothing wrong with it (it's not like it's adding a security risk or something)

---

### Post by Sniffer on 2004-12-06
Oki,

Thks, tought it would break my security.

---

### Post by macewan on 2004-12-23
[QUOTE=svarreby]I receive this message when I try to run Firestarter (from Applications -> Internet -> Firestarter Firewall Tool):

Failed to run /usr/sbin/firestarter as user root:
Wrong password.

..Eehhhh, am I missing some important info here ... :-)[/QUOTE]
 Just a quick/basic howto

Applications > Internet >

Right click on **Firestarter** and in the little window that appears you will want to click on the third choice down *Properties*. This will open a properties window, from here you change:

gksu /usr/sbin/firestarter

to

gksudo /usr/bin/firestarter

then click the **Close** button in the bottom right of this Launcher Properties window. Now when you click Applications > Internet > Firestarter and the password window appears you will not have problems after you input your password.

On a side note, the backported firestarter is verrrry nice.

Firestarter 1.0.0

:)

---

### Post by britishtrident on 2005-01-02
[QUOTE=jdong]use **gksudo firestarter**. Firestarter still is unchanged/unpatched... it assumes the existence of a root account.[/QUOTE]


I better hit this one on the head  the root account exist as on any normal  Debian  or nix system it is just that local and remote login to the root account are disabled.
Just about my first change to my ubuntu was enable local root logins from the start up screen, once I ge my syste fully configured I'll disable it again.

---

### Post by waveslider on 2006-04-22
I am having a similar problem. I am using ***gksudo firestarter*** but I am still getting the following error message:

[B]
Failed to run /usr/sbin/firestarter	 as user root:
 Child terminated with 1 status
[/B]

What can I do to fix this?

---

### Post by mjkey on 2006-04-23
[QUOTE=waveslider]I am having a similar problem. I am using ***gksudo firestarter*** but I am still getting the following error message:

[B]
Failed to run /usr/sbin/firestarter	 as user root:
 Child terminated with 1 status
[/B]

What can I do to fix this?[/QUOTE]
I am getting the same error as waveslider, any remedies?

---

### Post by RavenOfOdin on 2006-04-24
[QUOTE=mjkey]I am getting the same error as waveslider, any remedies?[/QUOTE]

That happened to me when I somehow got myself out of the admin group.

Check your /etc/group file.

---

### Post by waveslider on 2006-04-25
I checked my /etc/group file. My username is in both the 'adm' and the 'admin' groups. 

There is a 4 in front of my username in the adm group, and there is a 106 in front of my username in the admin group. Would that make a difference? Are there any other possible solutions to this problem?

Thanks!

---

### Post by lshawmd on 2006-04-28
[QUOTE=mjkey]I am getting the same error as waveslider, any remedies?[/QUOTE]

same problem as mjkey - any solutions?

---

### Post by waveslider on 2006-05-04
[QUOTE=waveslider]I am having a similar problem. I am using ***gksudo firestarter*** but I am still getting the following error message:

[B]
Failed to run /usr/sbin/firestarter	 as user root:
 Child terminated with 1 status
[/B]
[/QUOTE]


Does anyone know how to fix this? Does it mean that firestarter is not running?

---

### Post by yellowtrolley on 2006-05-07
My firestarter start ok from the Applications menu but not on Gnome startup.

I set the preferences on my Firestarter to start automatically on Gnome startup.
I get the "Child terminated with 1 status" error when Gnome starts.

I suppose it is because the process that start firestarter on gnome startup is not run with gksudo but I don't know how to fix it. 
Does anyone know?

---

### Post by lshawmd on 2006-05-07
[QUOTE=yellowtrolley]My firestarter start ok from the Applications menu but not on Gnome startup.

I set the preferences on my Firestarter to start automatically on Gnome startup.
I get the "Child terminated with 1 status" error when Gnome starts.

I suppose it is because the process that start firestarter on gnome startup is not run with gksudo but I don't know how to fix it. 
Does anyone know?[/QUOTE]

I managed to "solve" the problem by unchecking the 
Start/Restart firewall on program startup
in Preferences Firewall.   Hope this helps.

---

### Post by waveslider on 2006-05-09
[QUOTE=lshawmd]I managed to "solve" the problem by unchecking the 
Start/Restart firewall on program startup
in Preferences Firewall.   Hope this helps.[/QUOTE]

I tried this, but I am still getting the same error. Can anyone suggest another way to fix it?

Thanks!

---

### Post by meshback on 2006-05-21
[QUOTE=waveslider]I tried this, but I am still getting the same error. Can anyone suggest another way to fix it?

Thanks![/QUOTE]

What worked for me was removing the extra spaces after the word firestarter.  If you go to System > Preferences > Sessions.  Click on the Startup Programs tab, highlight the firestarter command and then click Edit.  If there are any extra spaces at the end of the command, delete them and click OK.  Worked fine after that.

Give that a try, might work for you.

---

### Post by bswilson on 2006-05-22
[SIZE="6"]Solution![/SIZE]

Friends, I had posted a similar question, and a kind user responded with the fix!  See [this thread]("http://ubuntuforums.org/showthread.php?t=163630") for details.

---

### Post by jpates20 on 2008-02-23
me to, can't run fire starter in gnome , i get this message/  Couldn't find package firestarter,

---

