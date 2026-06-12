---
title: "server GUI"
date: 2006-06-05
forum: Server Platforms
---

### Post by rsmiff on 2006-06-05
Will there be a release with a GUI? I'm tired of command line.

---

### Post by wthanna on 2006-06-05
sudo apt-get install ubuntu-desktop

now you have a gui!

---

### Post by kwaanens on 2006-06-05
Wouldn't OP maybe be more inclined to use Xfce, since he/she's running a server? That's what my server's running.

In that case:
sudo apt-get install xubuntu-desktop.

Requires much smaller applications, and uses the Xfce desktop environment, instead of Gnome.

- Ketil

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=rsmiff]Will there be a release with a GUI? I'm tired of command line.[/QUOTE]

why should a **server** need or run a GUI  (if you mean an X-Server when speaking about an GUI) ?! :confused:

Usually a server needs his resources to do his job, not run any X-Server. If you really need a GUI, use your desktop machine to do what you need (ie. test or lern how to configure your server) and use your desktop experiences for the server.

That's one advantage of this distribution .... use the Server release for your server and the Ubuntu/Kubuntu desktop release for your desktop machine. :)

Thomas

---

### Post by rsmiff on 2006-06-05
I knew I was going to get crap for this post. Thanks for the helpful responses.

---

### Post by Abild on 2006-06-05
You could also try out someting like webmin [http://www.webmin.com/](http://www.webmin.com/) It allows you to remotely administer your server from a browser without the commandline.

---

### Post by LordHunter317 on 2006-06-05
[QUOTE=linuxone]why should a **server** need or run a GUI  (if you mean an X-Server when speaking about an GUI) ?! :confused:[/quote]Oracle's installer and several of the admin tools need it.  So does some of the BEA WebLogic stuff, Sybase, I can think of a few other enterprise applications that are similarly behaved.

That being said, I tend to not install the X server on the box in question but rather the library and client stuff, and tunnel the server.  But installing FreeNX or VNC and doing it that way would also be a reasonable solution.

This whole "Servers shouldn't have GUIs" crap is total nonsense.  Certainly, the enterprise big guns don't feel that way.

---

### Post by jasonyu on 2006-06-05
I think you can install X on your server, after the necessary configuration, you can boot your server to run level 3, which runs under console rather than gui.

Is that better?

---

### Post by blkc4us on 2006-06-05
I tried to install webmin on ubuntu 6.06 server release using "sudo apt-get install webmin" but I couldn't get it. any ideas how?

---

### Post by LordHunter317 on 2006-06-06
[QUOTE=jasonyu]I think you can install X on your server, after the necessary configuration, you can boot your server to run level 3, which runs under console rather than gui.

Is that better?[/QUOTE]No, this is not RedHat.  X, once installed, will run at all runlevels by default.  You must manually select what runlevels you wish for it to run in.

---

### Post by NeoGreen on 2006-06-06
:confused:  Itried to install X on my server and kept getting an error message.  I guess I could try xubuntu desktopl.

---

### Post by A1ex on 2006-06-08
Webmin is no longer in the dapper repo's because the debian maintainer no longer maintains the package.

You'll have to download from [www.webmin.com](www.webmin.com) and run the install script. 

I believe other posts on the forum walk you through this.

---

### Post by kwaanens on 2006-06-08
[QUOTE=linuxone]why should a **server** need or run a GUI  (if you mean an X-Server when speaking about an GUI) ?! :confused:

Usually a server needs his resources to do his job, not run any X-Server. If you really need a GUI, use your desktop machine to do what you need (ie. test or lern how to configure your server) and use your desktop experiences for the server.[/QUOTE]

A server can be a number of things. I have a server that serves clients with files using Samba. I wouldn't think that the Xfce has a deadly impact on this server's ability to do its job, and with a desktop environment, it's easier for me to see what I'm doing.

- ketilø

---

### Post by linuxone on 2006-06-08
Hi,

[QUOTE=kwaanens]A server can be a number of things. I have a server that serves clients with files using Samba. I wouldn't think that the Xfce has a deadly impact on this server's ability to do its job, and with a desktop environment, it's easier for me to see what I'm doing.[/QUOTE]

this may finish in a philosophical discussion ... :-\"  But from my understanding of "servers" and the role of a server admin and also my own years of experiences as admin a server has nothing to do with a GUI.

Compare this meaning with the default setting of a Windows server: no users but ONLY accounts of the (Domain-) Admin group are allowed to login. Why? Because they should administrate the machine and nobody "use" it as work place. (and other reasons, of course)
Back to linux: a GUI is not needed to configure a text config file based system or programs. It might be helpfull when doing it the first few.... times, agreed, but finally it is not needed.

BTW, speaking about Samba a GUI is not needed, too. swat, the graphical Samba config tool, is Web based and can be used from any client machine in your network. :)

Thomas

---

### Post by jorgerosa on 2007-04-10
"I knew I was going to get crap for this post. Thanks for the helpful responses." - This is what you get and 1000s of people here, when you say the forbidden words "server" + "gui".
Sorry, i cant help you because i have same problem here.

Try this:
web-based: [http://ubuntuforums.org/showthread.php?t=405574](http://ubuntuforums.org/showthread.php?t=405574)
discuss: [http://ubuntuforums.org/showthread.php?t=401151&highlight=server+gui](http://ubuntuforums.org/showthread.php?t=401151&highlight=server+gui)
anoter discuss: [http://ubuntuforums.org/showthread.php?t=357600&highlight=server+guis](http://ubuntuforums.org/showthread.php?t=357600&highlight=server+guis) ---> you can find other distros with GUIs (my conclusion after read that post)

---

### Post by blueturtle1211 on 2007-08-07
I want to add a desktop to a server because I want to/hopefully can.  I'm doing it for experimental purposes.

I just installed 7.04 feisty fawn on an old COMPAQ Deskpro EN workstation because I want to make it into a router/proxyserver/firewall.  

The install was flawless.  

I have installed Dan's Guardian and SQUID to for their appropriate purposes.

I wanted to put kde desktop on it and ran the update: "sudo apt-get install kubuntu-desktop" to download the desktop.

After installing, I restarted the machine and booted up to a blinking cursor.  I used ctrl+alt+F1 to get back to command line.

I have edited my vga driver and monitor's vertical and horizontal refresh rates to their proper settings by vi editing the xorg.conf file, and verifying the changes.  

I still can't get the desktop to run.  All I end up with is a blinking cursor.  I'm stumped.:(


SPECS:

PIII 900MHz
8215 chipset
Hyundai X91D monitor
768MB RAM

Help would be great, but I understand that not everyone would put a desktop on a "server".  Please forgive me, die-hard linux server admins. :)

---

### Post by kerry_s on 2007-08-07
sudo apt-get install xorg gdm synaptic jwm menu mc
reboot(ctrl+alt+delete)

---

### Post by mzar on 2007-08-08
Using command line is better then GUI. Server not using to much resource when in command line. But sometime i using webmin to manage my server. So simple, just click and all done.

---

### Post by koenn on 2007-08-08
> **LordHunter317 said:**
> 
This whole "Servers shouldn't have GUIs" crap is total nonsense.  Certainly, the enterprise big guns don't feel that way.
I'd think enterprises lock their servers in a server romm / data center, never come near it (except for hardware trouble), and have their IT staff manage them remotely. Most of these servers don't even have monitors and keybords - they're just boxes in a rack

So either youhave client/server tools to admin it, or you export the display of GUI tools to a desktop machine, or you manage it from a command prompt. 
Therefore, servers don't need GUI's - or at least, don't need to be running a GUI environment.

---

### Post by mzar on 2007-08-08
Can you imagine the server that you want to manage far away from from your place, and you want to use GUI? :lolflag:

---

### Post by az on 2007-08-08
Installing ubuntu-desktop or any other desktop will not give you any tools to manage your web/database/mail servers.  

Webmin is pretty broken.

This looks like a good start.  It's a Google summer of code project:[https://wiki.ubuntu.com/UbuntuEasyBusinessServer](https://wiki.ubuntu.com/UbuntuEasyBusinessServer)

---

### Post by blueturtle1211 on 2007-08-08
After running "sudo apt-get install xorg gdm synaptic jwm menu mc" i chose kde from the choices and nothing happened.  I restarted, and still came up with the blinking cursor.

does anyone know a way to start a GUI from command line?

---

### Post by kerry_s on 2007-08-08
What do you mean you chose kde, that line does not install kde, it installs jwm. you say your at a blinking cursor, which means that even gdm didn't start. your install sounds really borked. gdm should start automaticaly.

what happens when you type> startx

---

### Post by Anteaus on 2007-08-08
> **blkc4us said:**
> I tried to install webmin on ubuntu 6.06 server release using "sudo apt-get install webmin" but I couldn't get it. any ideas how?

Reasonably sure  the .deb version from the Webmin site will do the trick. You might also need to manually install a few prerequisites.

BTW, I would never install kdm at the same time as the kdebase package. Test your GUI by issuing startx first. That way if it chokes on a wrong x11 config-value you can easily get out of trouble. If you cannot stop KDE from loading -and hanging- at startup, then try Alt-F1 to see if you can get a console open. Use this to edit your X11 config. If you can't then it's time to use the live-CD to edit the config. 

In fact, it's not even necessary to have KDE/Gnome/xfce installed to test the x-window-subsystem package. With no GUI installed, startx should give you a small graphics-mode console window, which you can close with 'exit.'

---

### Post by codmate on 2007-08-09
By the time you've managed to install the GUI, you will have learned so much about the command line, that you won't need the GUI any more  :p ;)

---

### Post by kerry_s on 2007-08-09
> **codmate said:**
> By the time you've managed to install the GUI, you will have learned so much about the command line, that you won't need the GUI any more  :p ;)

LOL! nothing wrong with command line, you can actually do alot with out X. i use mc for the filemanager, i browse the web with links2, all with out X.

---

### Post by coyote72 on 2007-08-19
Greetings all,
To those kind souls who have spent time helping and submitting responses to the question at hand, I thank you for your assistance.

To those who are behaving like techno-natzis who only critisize people cause they want to do something different and have a GUI, Keep loosing.

BTW I work in a mid to large size business that has more than 20 servers running. Unfortunately most of these are Win2k3 and are all managed remotely with a GUI. I have seen this in other places too.

Perhaps listening to the needs of the people will give you a greater understanding of what is needed and help to capture more of the marketplace.

I want more Linux servers at work but they want them to be GUI based for ease of maintaining for all admins.

Think on this!

Kind Regards
Coyote72

---

### Post by deuce868 on 2007-08-19
> **coyote72 said:**
> BTW I work in a mid to large size business that has more than 20 servers running. Unfortunately most of these are Win2k3 and are all managed remotely with a GUI. I have seen this in other places too.

Perhaps listening to the needs of the people will give you a greater understanding of what is needed and help to capture more of the marketplace.

I want more Linux servers at work but they want them to be GUI based for ease of maintaining for all admins.


Thought on it...nope. You can take screen, rsync, ssh tunneling, htop, vim, and tail after I'm long gone. 

It's funny, the people that clammer for gui's are usually the ones that haven't read the docs and want the gui to tell them how to set things up. The ones that actually set things up, tail the logs, and get things running tend to know what they're doing and have things running better and faster because of it. 

Look, get some books, learn the tools, and be better for it. If you run 20 windows boxes and have never had to go read through some AD books before you set it up, then I'd hate to see that network. If you want to setup samba, go get a samba (or insert linux daemon XX here) book and learn how to set it up correctly.

---

### Post by coyote72 on 2007-08-19
expected response. . .

closed mind, just like a parachute doesn't work!

I think you need to look at the philosophy of Ubuntu and consider it.

And I quote "linux for human beings"

Not for people who have been system administrators for 30 years and want to keep things the way they are with a big line seperating Ubuntu from being accessable and usable by people who have less skills at the time.

I hope that the actual people who are developing this very useful platform are reading the forums and listening to their fans.

Kind Regards
coyote72

---

### Post by deuce868 on 2007-08-19
> **coyote72 said:**
> expected response. . .
Not for people who have been system administrators for ***5*** years and want to keep things the way they are **because they've found it works much better than the windows gui world after living in both worlds.**


I figured I'd just at least make it correct.

---

### Post by coyote72 on 2007-08-19
Greetings all,
I appologise if my response earlier was a bit hasty and not worded well.

There are a few things that I would agree with you about,
A server when running and all is well does not need the overhead of gnome or any of the support modules running (you may say KDE or any other GUI).

And that a professional server would be admin'ed by someone who does know the CLI and how to get the best out of it.

I do happen to have quite a few Unix and Linux books and do know how to use a terminal. But the install of Ubuntu Server should give the user the option of installing a GUI for the user.

I want the potential of Linux realised and Microcrap put back in the box. A GUI will go a long way to getting there. Ubuntu has the best chance at the moment of cracking the MS strangle hold on the earth.

Meet the needs of the people and they will come!

Warm Regards

Coyote72

---

### Post by codmate on 2007-08-20
> **coyote72 said:**
> Greetings all,
I appologise if my response earlier was a bit hasty and not worded well.

There are a few things that I would agree with you about,
A server when running and all is well does not need the overhead of gnome or any of the support modules running (you may say KDE or any other GUI).

And that a professional server would be admin'ed by someone who does know the CLI and how to get the best out of it.

I do happen to have quite a few Unix and Linux books and do know how to use a terminal. But the install of Ubuntu Server should give the user the option of installing a GUI for the user.

I want the potential of Linux realised and Microcrap put back in the box. A GUI will go a long way to getting there. Ubuntu has the best chance at the moment of cracking the MS strangle hold on the earth.

Meet the needs of the people and they will come!

Warm Regards

Coyote72

It sounds as though you should just get Red hat Enterprise and pay for support, if you want a Linux replacement for Windows Server2003.

Even then you won't be able to drop the CLI.

One of the reasons you are seeing these responses to your question are that the GUI tools for configuring GNU/Linux are very hit-and-miss.
Some are more mature than others. Some use their own config files, rather than the system standard.

To a reasonably experienced *nix sysadmin, this lack of consistency isn't acceptable. Since there is no need to fight with extra tools, we just use the terminal to configure stuff as we have been doing for years.

If you have some good *nix books lying around, it may be an idea to read them. If you can spare the time I would suggest making a small network at home using GNU/Linux, and any other O/S, boxes to learn and practice. You'll have it nailed in about a fortnight.

My question to you would be, why are you fighting the CLI?
Sure - regular users need a GUI these days. It's the generally accepted 'user environment'.

Even on Windows, we sysadmins still regulalrly open up a CLI. Hell - why do you think MS released PowerShell?! It's less critical than it is with *nix - but still pretty damn important!

If I were hiring sysadmins, and somebody couldn't use the command-line, be it *nix or Windows, they wouldn't get the job.
End of story.

You also make the point that more people would move to Linux if the GUI tools were more solid for the server admin stuff. This is simply not the case. People who are serious about administering *nix systems read books and go on courses to learn the command-line tools; just as people read books and go on courses to learn how to administer Windows 2003 boxes using their mixture of GUI and CLI tools.

Did you really expect to change to an entirely different server O/S without doing any work or learning new things?

Again - I say that this is wholly different for a 'regular user'. Since a GUI is their natural environment; Ubuntu desktop caters for them brilliantly.

Since the 'natural environment' of a *nix sysadmin is still the CLI, this is what is provided as default. Install a GUI on top of it and use the config tools if you like. Doing this will benefit us all as you will be helping the development of those GUI tools by using them and reporting back to the developers. But bear in mind what I said before - those tools are not wholly mature, and there isn't a complete 'suite' of them that allows you to administer your system in the way you want.

If you are *really* keen to improve the whole 'admin via the GUI' thing in Linux, you will learn to program these GUI's for yourself and join the dev teams for them. This is the way of open source. We don't moan and whine that the tools aren't there - we create them! But only if we need them  ;)

It's actually a testament to the efficiency of the command line that GUI tools don't exist for many things in Linux! We didn't write them because we don't need them!

I would encourage you to persevere for a month at least with the  command line.

First read up on how to use bash efficiently.
Learn how to use its history features (CTRL+R is very useful ;) ).
Install and learn how to use screen - this can be invaluable!
Learn about Unix permissions - they are very simple and effective!
Learn about adding and removing users and groups using 'useradd', 'groupadd' and 'usermod'.
Learn about networking using ifconfig.
Check out Samba for file-sharing.

Remember - you are not alone, we are here to help and it's not that hard!

---

### Post by coyote72 on 2007-08-20
Thank you Codemate, your response is very well thought out and considerate.
I may well in the future head in the Developer direction, as I see a need for these GUI tools for people who want the ease of that environment.

I am extreamly excited about Ubuntu and like the CLI in it as much as I do the cmd on windows and way back to my old dos days (I could really turn out a batch file in 5.1).

I will perservear with the CLI on Fiesty Fawn and have it in time. It will be a LAMP install possibly with Samba added in. Time will tell.

By the by, I was previously running Redhat 9.1 and have done a couple of re compiles on that, so I am not quite a noob. But that was over six months ago and the brain gets a bit rusty without exercise. hehehe

again thank you.

Coyote72

---

