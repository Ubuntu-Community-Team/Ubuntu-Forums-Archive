---
title: "This is what I did - Wine did NOT install   1. Click Application&gt;Accessories&gt;Terminal"
date: 2009-06-22
forum: Wine
---

### Post by dailyacts56 on 2009-06-22
[LIST=1]
[*]Click     Application>Accessories>Terminal
[*] On the Terminal     window type ‘wine –version’
     If you have not     installed wine yet you will receive this message then you may     proceed to step 4.
[/LIST]
 [COLOR=#800000]'[SIZE=2]*T*[/SIZE][SIZE=2]*he program 'wine' is currently not installed.  You can install it by typing: *[/SIZE][/COLOR]
 [COLOR=#800000][SIZE=2]*sudo apt-get install wine *[/SIZE][/COLOR]
 [COLOR=#800000][SIZE=2][I]bash: wine: command not found'

[/I][B]After that, it asked for a password. I tried to use the only password I ever use. It did not accept the password and it did NOT install.

That is everything I did.

Someone in the group said NOT to use sudo. 

Help me install and use wine.

Thank you!
[/B][/SIZE][/COLOR]

---

### Post by jhoeijao on 2009-06-22
> **dailyacts56 said:**
> 
[LIST=1]
[*]Click     Application>Accessories>Terminal
[*] On the Terminal     window type &#8216;wine &#8211;version&#8217;
     If you have not     installed wine yet you will receive this message then you may     proceed to step 4.
[/LIST]
 [COLOR=#800000]'[SIZE=2]*T*[/SIZE][SIZE=2]*he program 'wine' is currently not installed.  You can install it by typing: *[/SIZE][/COLOR]
 [COLOR=#800000][SIZE=2]*sudo apt-get install wine *[/SIZE][/COLOR]
 [COLOR=#800000][SIZE=2][I]bash: wine: command not found'

[/I][B]After that, it asked for a password. I tried to use the only password I ever use. It did not accept the password and it did NOT install.

That is everything I did.

Someone in the group said NOT to use sudo. 

Help me install and use wine.

Thank you!
[/B][/SIZE][/COLOR]

Download wine from this site [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) choose 1.1.24 the latest version that fixed the regression issue in installing MSOFFICE because I think you are trying to installl MSOFFICE 2007.

Note: "wine --version" not "wine -version"

EDIT:
and there are three ways in installing wine

1. Using Synaptic Package Manager
2. Using the Terminal
3. Downloading it and install

Just click this site for further explanation and how to install wine [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by donkyhotay on 2009-06-22
> **dailyacts56 said:**
> [LIST=1]

Someone in the group said NOT to use sudo. 

[/B][/SIZE][/COLOR]

Sudo is a tool like a knife, it can be very useful tool but it also can be very dangerous (especially if you don't know what you're doing). That doesn't mean you should never ever use it, just means you need to be careful. If you're ever in doubt do not use sudo and ask someone first (these forums are a good place until you get a feel for it). In this particular instance you will need to use sudo in order to install wine. Although the previous poster is correct in stating downloading wine from winehq will help with compatibility with recent programs, it is also a little harder (for some people) to install. The easiest (in my opinion at least) way to install wine is to use the terminal. If you choose to do this just copy and paste
```

sudo apt-get install wine

```
which is the exact command to install from terminal.

---

### Post by NightMKoder on 2009-06-22
Downloading the file directly won't notify you of future upgrades. Use [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) to get updates.

In most cases when you need to install something (commands like `sudo apt-get ...` or `sudo aptitude`) it is safe to enter your password (after all you are installing something). 

On the other hand if something doesn't work with >>wine<< itself (ie some windows app crashes), some people decide that sudo is the `answer to life the universe and everything` and use commands like `sudo wine ....exe`, which under normal circumstances will tell you that you're doing something bad, but if persistent, you can ruin your wine install.

---

### Post by JeshiBrat on 2010-03-10
[COLOR=DarkRed][COLOR=Black]Following the instructions on WineHQ.org, I got the following message.  I even installed Scott Ritchie's key for good measure after the installation didn't work the first time:[/COLOR]
[B]
Invalid /etc/apt/sources.list file[/B]
E:Type 'n' is not known on line 2 i source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list, E:The list of sources could not be read.[/COLOR]

[COLOR=Black]I had no problems installing Wine on the previous Ubuntu version.  Please help.  Or is there some other software that will allow me to open a MS Access database in Linux?[/COLOR]

---

### Post by Soulcage on 2010-03-12
@JeshiBrat
Are you on Karmic if you are you can paste into a terminal:

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.2

If you aren't then you should make sure you read the right instructions for your version of ubuntu.

---

