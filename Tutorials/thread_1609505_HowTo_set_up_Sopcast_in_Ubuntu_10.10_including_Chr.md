---
title: "HowTo: set up Sopcast in Ubuntu 10.10 including Chromium sop links"
date: 2010-10-30
forum: Tutorials
---

### Post by ryukent on 2010-10-30
To install sopcast player you need to add the following repository. ([Thanks to Roberto @ llfl]("http://www.lffl.org/2010/10/installiamo-sopcast-042-su-ubuntu-1010.html"))

```
sudo add-apt-repository ppa:ferramroberto/sopcast
sudo apt-get update
```

Then, install sopcast-player as follows:

```
sudo apt-get install sopcast-player
```

Finally you will need to set up Chrome (Chromium) to link to sopcast links from websites.

```
gconftool-2 –set –type=string /desktop/gnome/url-handlers/sop/command ‘sopcast-player “%s”‘
gconftool-2 –set –type=bool /desktop/gnome/url-handlers/sop/enabled true
gconftool-2 –set –type=bool /desktop/gnome/url-handlers/sop/need-terminal false
```

You can now enjoy moments like seeing Arsenal score in the 87th minute against West Ham like I just did thanks to our favourite p2p website in the EU.

[From my blog]("http://www.ryukent.co.uk/2010/10/howto-set-up-sopcast-in-ubuntu-10-10-including-chromium-sop-links/")

---

### Post by FokkerCharlie on 2010-11-02
Hi Rukent

Thanks for posting your instructions.  I couldn't get the chromium links to work, however.  Any suggestions?

Charlie

---

### Post by ryukent on 2010-11-07
> **FokkerCharlie said:**
> Hi Rukent

Thanks for posting your instructions.  I couldn't get the chromium links to work, however.  Any suggestions?

Charlie

Can you give me some more information? Are you able to watch any channels in SopCast player? 

If you copy the link and paste it into the open dialogue box in SopCast player does it load?

If you click on a SOP link in Chromium, does it launch SopCast player?

---

### Post by FokkerCharlie on 2010-11-07
Hi ryukent

Thanks for your response, and my apologies for not providing more information in the first place.

I can play sopcast videos fine by copy/paste into gsopcast.  Clicking a sopcast link in Chromium opens a new, empty tab in the browser, and does not launch sopcast.  If sopcast is already running, it doesn't seem to notice, so no joy there either.

Cheers
Charlie

---

### Post by ryukent on 2010-11-09
Right, you've just told me that you are using gsopcast. The instructions above are to run the link in sopcast-player, which is a totally different program than gsopcast. I don't even know if gsopcast supports link parsing. If you install sopcast-player then the link handler should launch it. You could try changing the command to gsopcast, but it would depend on that program having sop link functionality from the command line.

Try running gconf-editor and having a look in  /desktop/gnome/url-handlers/sop/

You want the command to include a program that you could run in the terminal with the sop link as a parameter.

---

### Post by FokkerCharlie on 2010-11-11
Hi Ryukent

My apologies for the confusion, I do actually have sopcast-player installed, not gsopcast.  I think that was a previous version or something I used a while ago.  Not sure.  Anyway, the problem is not solved for me.

However, looking in gconf-editor, there is no sop under url-handlers.  I have run the gconftool-2 commands you mentioned again, with no good result.

How strange!  Any ideas?

Charlie

---

### Post by ryukent on 2010-11-15
Hmm, this is strange. You didn't run them as sudo did you? Also, are you running standard ubuntu (not kde etc)?

> **FokkerCharlie said:**
> Hi Ryukent

My apologies for the confusion, I do actually have sopcast-player installed, not gsopcast.  I think that was a previous version or something I used a while ago.  Not sure.  Anyway, the problem is not solved for me.

However, looking in gconf-editor, there is no sop under url-handlers.  I have run the gconftool-2 commands you mentioned again, with no good result.

How strange!  Any ideas?

Charlie

---

### Post by FokkerCharlie on 2010-11-15
Hy Ryukent

No, I did not run as sudo, and am using normal vanilla Ubuntu.

There are no error messages in the terminal when I enter the commands.  Can I enter the keys in gconf-editor?  If so, it's not clear to me how...

Cheers
Charlie

---

### Post by anaspeople on 2010-11-29
Remender that
```
gconftool-2 –set –type=string /desktop/gnome/url-handlers/sop/command ‘sopcast-player “%s”‘
```
is supposed to be:
```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/sop/command 'sopcast-player "%s"'
```
and so on.

---

### Post by dr.twinny on 2010-12-26
[QUOTE=ryukent;10048586]```

Finally you will need to set up Chrome (Chromium) to link to sopcast links from websites.

[CODE]gconftool-2 –set –type=string /desktop/gnome/url-handlers/sop/command ‘sopcast-player “%s”‘
gconftool-2 –set –type=bool /desktop/gnome/url-handlers/sop/enabled true
gconftool-2 –set –type=bool /desktop/gnome/url-handlers/sop/need-terminal false
```/QUOTE]

Thanks. I got Sopcast installed, but how do i go about setting up these links??

---

### Post by woyzeckswoe on 2011-01-17
thanks a lot everybody, works flawlessly and the link opener for chromium comes in pretty handy.
just so thats a little easier for copy paste:

```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/sop/command 'sopcast-player "%s"'
gconftool-2 --set --type=bool /desktop/gnome/url-handlers/sop/enabled true
gconftool-2 --set --type=bool /desktop/gnome/url-handlers/sop/need-terminal false
```

---

### Post by ideamaestro on 2011-01-22
Many thanks to the OP. It works flawlessly and the video quality is outstanding really!!!

Just one question. How do I record a stream? I tried changing the player from mplayer to vlc, but the skin is the same. I guess the engine is different.

Please help me with this one! Would be cool to record Champions League finals!

If this is not the right thread, MODs, could you please shift this to an appropriate thread? Thanks.

---

### Post by brutus83 on 2011-03-10
thanks to ryukent, and anaspeople.
It works ! :D

---

### Post by dragon99 on 2011-04-07
[QUOTE=ryukent;10048586]To install sopcast player you need to add the following repository. ([Thanks to Roberto @ llfl]("http://www.lffl.org/2010/10/installiamo-sopcast-042-su-ubuntu-1010.html"))

```
sudo add-apt-repository ppa:ferramroberto/sopcast
sudo apt-get update
```

Then, install sopcast-player as follows:

```
sudo apt-get install sopcast-player
```


I pickup the repo ok, but when I run the code to install sopcast player I get the following error:

paul@moe:~$ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sopcast-player

Is there a problem within the repos? Is there an alternate source I can try?

dragon

---

### Post by woyzeckswoe on 2011-05-24
@dragon

you could try this other repo
works for me

[https://launchpad.net/~jason-scheunemann/+archive/ppa](https://launchpad.net/~jason-scheunemann/+archive/ppa)

---

### Post by Cyr4x on 2011-08-16
Doesn't work for dev Chrome 14 (not Chromium!). It opens sopcast links via xdg-open and it says this type of link is not supported :(

---

### Post by bgmainx on 2011-08-22
Huge thanks for this! I wasn't aware that sopcast works with linux (thought only through wine, which I hate).

---

### Post by lpwaqas on 2011-08-28
These installation instructions worked for me :) check them out.



echo "deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu)  `lsb_release -cs` main" | sudo tee -a /etc/apt/sources.list &&  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56 
Now that the repositories are installed issue the following commands to install sopcast-player: 
sudo apt-get update && sudo apt-get install sopcast-player 
In  certain countries you may need to install the Medibuntu repositories to  satisfy the VLC dependency requirement. Use the following command to  install the version of Medibuntu relevant to your Ubuntu release: 
sudo  wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo  apt-get -q update && sudo apt-get --yes -q  --allow-unauthenticated install medibuntu-keyring && sudo  apt-get -q update

---

### Post by chondromalasia on 2011-09-18
Hello, I'm trying to install sopcast and I'm running into some weird problems. So, I've added this ppa: ppa:jason-scheunemann/ppa and this is what I get:


Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv B7A54DFD57990DE60964F52D932062C9CD30EE56
gpg: requesting key CD30EE56 from hkp server keyserver.ubuntu.com
gpg: key CD30EE56: "Launchpad PPA for flyguy97" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Then when I apt-update, I get this:


W: Failed to fetch [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/katya/main/source/Sources](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/katya/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/katya/main/binary-i386/Packages](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/katya/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/katya/main/source/Sources](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/katya/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/katya/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/katya/main/binary-i386/Packages)  404  Not Found


ferramroberto is another guy that supposedly hosts the sopcast packages.

then when I try to apt-gen install sopcast it tells me that the sopcast packages can't be found.

I'm running katya if that helps.

Thanks!

---

### Post by Johanu on 2012-04-22
I've managed to make it work with Chrome 18.0.1025.162 and Ubuntu 11.10, so I hope this is useful to you. Simply adding the previous url handlers didn't work for me, so I had to dig around a bit until I got it to work. 

You have to add a sopcast-player.desktop file inside ~/.local/share/applications configured in this manner:

```
[Desktop Entry]
Name=Sopcast Player
Exec=sopcast-player %u
Icon=sopcast.icon
Type=Application
Terminal=false
MimeType=x-scheme-handler/sop;
```

Then, you have to configure mimeapps.list and add the sopcast-player.desktop to your Added Associations. Like this:

```
[Added Associations]
x-scheme-handler/sop=sopcast-player.desktop;
```

After that all should be working. When you press a sop:// link in Chrome/Chromium it should launch the sopcast player and start connecting to the channel.

---

