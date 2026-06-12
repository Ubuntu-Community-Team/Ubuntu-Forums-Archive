---
title: "Galaxium Messenger"
date: 2008-05-05
forum: The Cafe
---

### Post by atomkarinca on 2008-05-05
(There is an old post about this from 2006 but the thread seems to have been closed so somebody had to do this)

It's a very promising IM application. Here are its features:

> **Available Features:**
[LIST]
[*]Contact List Management 
[*]Personalized content (Display Pictures, Personal Messages, Custom Emoticons) 
[*]Indirect File Transfers (MSN) 
[*]Direct File Transfers (Jabber wo/NAT only) 
[*]MSN and Jabber (+GTalk) Session Support 
[*]MSN communication with Yahoo contacts 
[*]MSN over HTTP protocol 
[*]Adium Theme Support 
[*]GStreamer Audio Support 
[*]Group Chat 
[*]Offline Messaging (MSN) 
[*]Roaming Profiles (MSN)
[/LIST]
**In-Progress Features:**
[LIST]
[*]IRC Session Support 
[*]Conversation History Tracking 
[*]Direct File Transfers (MSN, Jabber w/NAT, IRC) 
[*]**Audio/Video Conversations **
[*]NAT Traversal through uPNP Routers
[/LIST]
**Planned Features:**
[LIST]
[*]AIM/**ICQ** and Yahoo Session Support 
[*]Integration with music players like Banshee, Rhythmbox, etc. 
[*]Integration with the GNOME desktop, nautilus, etc.
[/LIST]

First of all I think it's good news for us, Ubuntu users. Why? I think there are two reasons why Pidgin comes preinstalled with Ubuntu:
- Supports multiprotocol,
- "Interacts well with GNOME"

Since developers of Galaxium are trying to make it interact well with GNOME then only problem is being multiprotocol. For now Galaxium supports MSN and Jabber (and Gtalk obviously). But they are trying to add ICQ, AIM, Yahoo and IRC support. What is amazing is that **they are actually working on a/v support**.

Only down side -for me- is that it's a .NET application. But since Ubuntu includes Tomboy in the live cd why not include this one?

Oh and I forgot, here's the website: [http://code.google.com/p/galaxium/]("http://code.google.com/p/galaxium/")

---

### Post by FuturePilot on 2008-05-05
That looks pretty cool. I like the layout. I might just try that.

---

### Post by atomkarinca on 2008-05-05
For future reference, here's how you install it:

Open up your sources list and add the appropriate repository

```
gksudo gedit /etc/apt/sources.list
```

For Gutsy:

```
deb http://ppa.launchpad.net/paulburton89/ubuntu gutsy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu gutsy main
```

For Hardy:

```
deb http://ppa.launchpad.net/paulburton89/ubuntu hardy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu hardy main
```

then update and install:

```
sudo apt-get update
sudo apt-get install galaxium
```

---

### Post by billgoldberg on 2008-05-05
> **atomkarinca said:**
> For future reference, here's how you install it:

Open up your sources list and add the appropriate repository

```
gksudo gedit /etc/apt/sources.list
```

For Gutsy:

```
deb http://ppa.launchpad.net/paulburton89/ubuntu gutsy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu gutsy main
```

For Hardy:

```
deb http://ppa.launchpad.net/paulburton89/ubuntu hardy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu hardy main
```

then update and install:

```
sudo apt-get update
sudo apt-get install galaxium
```

Thanks, I'll give it a try.

---

### Post by vishzilla on 2008-05-05
I have heard about this. There are two IM projects that have interested me. First its Galaxium and another one is GNOME's Empathy. Both are somewhat in the same stage of development.

---

### Post by billgoldberg on 2008-05-05
I installed it, started it and watched how it failed to connect to my msn account.

Then I got a scare from the sounds it produces (sound was turned up high).

It grayed out, and all of the sudden it was connected.

The program looks pretty good.

But I think I'll stay with "emesene".

---

### Post by atomkarinca on 2008-05-05
> **billgoldberg said:**
> But I think I'll stay with "emesene".

I second that. But it's shaping to be the IM application every noob is looking for, that's why I'm keeping it.

---

### Post by Sef on 2008-05-05
There is a note there about the repositories:  **The repositories are currently BETA**.

---

### Post by Foster Grant on 2008-05-05
No AIM? Fuhggedaboutit.

---

### Post by Nevon on 2008-05-05
> **billgoldberg said:**
> I installed it, started it and watched how it failed to connect to my msn account.

Then I got a scare from the sounds it produces (sound was turned up high).

It grayed out, and all of the sudden it was connected.

The program looks pretty good.

But I think I'll stay with "emesene".

Same exact thing happened here. If they get that darn webcam support going, and fix those issues it seems to have with MSN, then this could definitely replace Pidgin for me (even though I *really* like Pidgin)

---

### Post by bash on 2008-05-05
Wow ... that project still exists. I checked them out back in '06 when their page was still hosted at bountysource.com. The project seemed to be slowly dieing back then - the only thing active were spam bots on the forum.

But this looks pretty neat especially if the manage to get multi-protocol (what pidgin has) plus the special per protocol feature richness (what pidgin never seems to get).

/edit:

Justed tested the new version. Sadly sending and recieving MSN messages seems to be as unstable as 2 years ago. Messages still randomly "vanish" without you or the other contact knowing. And it crashes quite a bit.

---

### Post by HangukMiguk on 2008-05-05
I'm not sure how tough it would be for them to just use the libpurple protocols and just work on their own gui (including the use of adium themes), and then just create a/v support and send it back to purple.

That idea makes more sense to me.

---

### Post by burty89 on 2008-05-14
> **bash said:**
> Justed tested the new version. Sadly sending and recieving MSN messages seems to be as unstable as 2 years ago. Messages still randomly "vanish" without you or the other contact knowing. And it crashes quite a bit.

Hi, I work on Galaxium and wrote large parts of the current MSN protocol code. I'm sorry to hear it didn't work very well for you, maybe you could [file a bug report]("http://code.google.com/p/galaxium/issues/entry") to help us figure out why it failed/crashed? If you do so then the output from the debug window or from a terminal would be helpful to attach to the report.

---

### Post by Wanas on 2008-06-08
sorry I'm new to linux where i put the code exactly plz i want to use this messenger

---

### Post by burty89 on 2008-06-08
> **Wanas said:**
> sorry I'm new to linux where i put the code exactly plz i want to use this messenger

The repository for Galaxium changed earlier today, it's now located at [https://launchpad.net/~galaxium/+archive](https://launchpad.net/~galaxium/+archive)

Basically, if you use Ubuntu hardy, you need to add the following to /etc/apt/sources.list

```
deb http://ppa.launchpad.net/galaxium/ubuntu hardy main
deb-src http://ppa.launchpad.net/galaxium/ubuntu hardy main
```

Or you can add it in synaptic through Settings->Repositories->Third Party Software. You then click add and enter one of the lines from above, click OK, then click add again for the other line.

Finally apt-get update or reload in synaptic and install the galaxium-svn package.

(If you use gutsy just replace hardy with gutsy above)

---

### Post by gumjo on 2008-06-21
> **burty89 said:**
> Hi, I work on Galaxium and wrote large parts of the current MSN protocol code. I'm sorry to hear it didn't work very well for you, maybe you could [file a bug report]("http://code.google.com/p/galaxium/issues/entry") to help us figure out why it failed/crashed? If you do so then the output from the debug window or from a terminal would be helpful to attach to the report.

Just want to say that Galaxium Messenger is a great program! Hope you keep improving on it. I replaced Emesene and Pidgin with it. :guitar:

---

### Post by Mateo on 2008-06-21
What are its advantages over Pidgin?

---

### Post by burty89 on 2008-06-21
> **Mateo said:**
> What are its advantages over Pidgin?

Essentially, whilst we are working to support multiple protocols, we are also working to support the extra bits such as nudges, winks, fast transfers, audio/video etc that Pidgin never seems to deliver.

Also each protocol is free to extend the GUI or even replace parts of it such as its chat area & contact list should it need to present things differently, although we do keep most of it common to provide some consistency.

The GUI is also different in a number of ways you can probably see best by looking at some [screenshots]("http://code.google.com/p/galaxium/wiki/Screenshots").

There's also the fact that I think we have the best implementation of the MSN P2P protocol (responsible for display pics/winks/file transfers etc), but I guess I'm biased having written it :)

---

### Post by billgoldberg on 2008-06-21
> **Mateo said:**
> What are its advantages over Pidgin?

The one that most people care about, decent avatar support.

moehahah

Note: Galaxium got a lot of updates, and it runs pretty good now.

I'm using it on my desktop all the time.

There is a small glitch that bugs me, sometimes the text stops appearing and you have to type blind.

---

### Post by Mateo on 2008-06-21
ok, thanks for the information.  i'm happy with pidgin as it seems that the advantages are not stuff that is important to me (don't use the msn protocol and don't care about avatars).  good luck nonetheless.

---

### Post by pencilcheck on 2008-06-28
I can't make adium theme to work. I receive the message "unable to create adium message"

---

### Post by burty89 on 2008-06-28
> **pencilcheck said:**
> I can't make adium theme to work. I receive the message "unable to create adium message"

I replied to your post on our google group (at [http://groups.google.com/group/galaxium/t/362ea9b57a3087bb]("http://groups.google.com/group/galaxium/t/362ea9b57a3087bb") for anyone else interested)

---

### Post by MadsRH on 2008-06-28
Maybe this is a dumb question but, how do I uninstall it??? :confused:

---

### Post by burty89 on 2008-06-28
> **MadsRH said:**
> Maybe this is a dumb question but, how do I uninstall it??? :confused:

Run synaptic, find the package, right click it and select remove. Then apply your changes.

---

### Post by MadsRH on 2008-06-28
synaptic! Of course - I was looking in add/remove ](*,) and could not uninstall it from the terminal

Thanks :)

---

### Post by Orwell on 2008-08-06
I've just recently installed this myself after finding aMSN to be a bit of a pain. One thing I'm interested to know is how/if at all, can I get my "Now Playing" tracks to appear as they did in the bad-old-days of msn?

At present I'm using Banshee as my media player...if that's of any consequence...

---

### Post by Hells_Dark on 2008-08-06
Adium themes !
Awesome. This IS my next IM.

---

### Post by bash on 2008-08-06
I currently use the svn version which already has the in-progress features integrated and it is a real nice client.

Just do:

```
sudo apt-get install galaxium-svn
```

to install the svn version. But remember: It's svn. So don't wonder if what you get is b0rked. Don't complain then but contribute bug reports!

---

### Post by Hells_Dark on 2008-08-06
How to use yahoo ? (svn)

---

### Post by HansKisaragi on 2008-08-06
Sweet, i'm running the svn version now .. looks nice, think i will use it for a while and see how it is.

---

### Post by RATM_Owns on 2008-08-07
Piss. It's sucking. And I really like this.

When I install galaxium and try and use it (from the menu and terminal) it doesn't work. So I purged that and tried galaxium-svn, but instead since I chose to automatically log in one time it stays at the log in screen and everything is grayed out so I can't choose anything.

So, help please?

---

### Post by Orwell on 2008-08-13
I've recently started using Galaxium and I love it. One question I do have though, is there any plugin for displaying my currently playing track?

Cheers!

---

### Post by the guitarist on 2008-08-13
can anyone tell me how can i add adium themes to galaxium ?!

---

### Post by Joe_Bishop on 2008-08-19
> **Orwell said:**
> I've recently started using Galaxium and I love it. One question I do have though, is there any plugin for displaying my currently playing track?

Cheers!
I tried it. It's very nice and fast, but also is quite hard in use - its non intuitive and lacks of many essential features gajim has. History, for example. After try it and switch back to gajim I felt myself like flying.

---

### Post by kirsis on 2008-08-19
> **Orwell said:**
> I've recently started using Galaxium and I love it. One question I do have though, is there any plugin for displaying my currently playing track?

Cheers!

Install the galaxium-svn version. It adds support for GTalk, Jabber and IRC + has an addin for this (currently playing) functionality.

---

### Post by RATM_Owns on 2008-08-19
Is there a settings folder or something for Galaxium?

Because I purged Galaxium a couple times and galaxium doesn't work at all, but galaxium-svn works but it won't show the buddy list. Freezes at logging in because I chose to log in automatically.

---

### Post by luisneto on 2008-08-19
Well, i've been using this IM for a week or so, i quite like it but i have a question. How do i copy a smile from the person i'm talking to? It looks like i only can add smiles from a image file. I also tried to add a different emoticons pack, which didn't wen't well.

Any ideas?

Thanks

---

### Post by atomkarinca on 2008-08-19
> **RATM_Owns said:**
> Is there a settings folder or something for Galaxium?

Because I purged Galaxium a couple times and galaxium doesn't work at all, but galaxium-svn works but it won't show the buddy list. Freezes at logging in because I chose to log in automatically.

It should be ~/.config/Galaxium

---

### Post by the guitarist on 2008-08-28
hello everyone,

i installed galaxium but whenever i try to log in it freezes at the synchronizing step ?

please help ...

i've been trying to find a solution forever

---

### Post by atomkarinca on 2008-08-29
> **the guitarist said:**
> hello everyone,

i installed galaxium but whenever i try to log in it freezes at the synchronizing step ?

please help ...

i've been trying to find a solution forever

Have you tried galaxium-svn?

---

### Post by the guitarist on 2008-08-30
> **atomkarinca said:**
> Have you tried galaxium-svn?

yes i did..and the same thing happend...but I've got it working now...i've build it from source and compiled it and it's working just fine write now..

but i really wanna try the latest svn version ... where can i find the source folder so i would build it on my machine my self?

sorry for my bad english

---

### Post by monikgtr on 2009-11-23
> **the guitarist said:**
> can anyone tell me how can i add adium themes to galaxium ?!

Go to Adium Xtras and download any theme you want, then copy the .zip (all the themes I've downloaded from [http://www.adiumxtras.com](http://www.adiumxtras.com) are in .zip format) into your /home/user/.config/Galaxium/Themes/AdiumMessageStyles

Restart Galaxium and there you go! :D

Also, for emoticon themes, the path is /home/user/.config/Galaxium/Themes/AdiumEmoticons

---

### Post by nainif82 on 2009-11-23
> **atomkarinca said:**
> For future reference, here's how you install it:

Open up your sources list and add the appropriate repository

```
gksudo gedit /etc/apt/sources.list
```

For Gutsy:

```
deb http://ppa.launchpad.net/paulburton89/ubuntu gutsy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu gutsy main
```

For Hardy:

```
deb http://ppa.launchpad.net/paulburton89/ubuntu hardy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu hardy main
```

then update and install:

```
sudo apt-get update
sudo apt-get install galaxium
```

Hi there, i am new here and also i am trying do as above but the result is as below....

```
zulkarnain@zulkarnain-laptop:~$ gksudo gedit /etc/apt/sources.listzulkarnain@zulkarnain-laptop:~$ sudo apt-get update
Hit http://my.archive.ubuntu.com hardy Release.gpg                             
Ign http://my.archive.ubuntu.com hardy/main Translation-en_US                  
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://my.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://my.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://my.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://my.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://my.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://my.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://my.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://my.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://packages.medibuntu.org hardy Release                                
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://my.archive.ubuntu.com hardy Release                                 
Hit http://my.archive.ubuntu.com hardy-updates Release                         
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://my.archive.ubuntu.com hardy/main Packages                           
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://my.archive.ubuntu.com hardy/restricted Packages                     
Hit http://my.archive.ubuntu.com hardy/main Sources                            
Hit http://my.archive.ubuntu.com hardy/restricted Sources                  
Hit http://my.archive.ubuntu.com hardy/universe Packages                   
Hit http://security.ubuntu.com hardy-security/universe Sources             
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://my.archive.ubuntu.com hardy/universe Sources                        
Hit http://my.archive.ubuntu.com hardy/multiverse Packages                 
Hit http://my.archive.ubuntu.com hardy/multiverse Sources
Hit http://my.archive.ubuntu.com hardy-updates/main Packages
Hit http://my.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://my.archive.ubuntu.com hardy-updates/main Sources
Hit http://my.archive.ubuntu.com hardy-updates/restricted Sources
Ign http://ppa.launchpad.net hardy Release.gpg 
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Hit http://my.archive.ubuntu.com hardy-updates/universe Packages
Hit http://my.archive.ubuntu.com hardy-updates/universe Sources
Hit http://my.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://my.archive.ubuntu.com hardy-updates/multiverse Sources
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Get:2 http://ppa.launchpad.net hardy/main Packages [94B]
Get:3 http://ppa.launchpad.net hardy/main Sources [89B]
Fetched 27.8kB in 5s (5080B/s)
Reading package lists... Done
zulkarnain@zulkarnain-laptop:~$ sudo apt-get install galaxium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package galaxium

```

anyone please explain to me or tell me why? and also my irc also not working which is i am trying to connect but it won't. i am using pidginIM.

TQ

---

### Post by ugm6hr on 2009-11-24
> **nainif82 said:**
> Hi there, i am new here and also i am trying do as above but the result is as below....

anyone please explain to me or tell me why? and also my irc also not working which is i am trying to connect but it won't. i am using pidginIM.

TQ

Post the contents of /etc/apt/sources.list - I think that may the problem.

---

### Post by nainif82 on 2009-11-26
> **ugm6hr said:**
> Post the contents of /etc/apt/sources.list - I think that may the problem.

Meaning? would you please explain more details? 

TQ
:???::???:

---

### Post by venator260 on 2009-11-26
To post the sources list:


1. Open a terminal
2. Type gedit /etc/apt/sources.list
3. Copy the contents of that file
4. Paste them here

The reason for this would be that, because Apt cannot find the package, it stands to reason that you may have not added the correct repository to your sources list. If we see your sources list, we can see if that is, in fact, the case.

---

### Post by nainif82 on 2009-11-27
```
zulkarnain@zulkarnain-laptop:~$ sudo gedit/etc/apt/sources.list
[sudo] password for zulkarnain: 
sudo: gedit/etc/apt/sources.list: command not found
zulkarnain@zulkarnain-laptop:~$ 

```

i do as explain but still can't get it......

---

### Post by jonian_g on 2009-11-27
> **nainif82 said:**
> ```
zulkarnain@zulkarnain-laptop:~$ sudo gedit/etc/apt/sources.list
[sudo] password for zulkarnain: 
sudo: gedit/etc/apt/sources.list: command not found
zulkarnain@zulkarnain-laptop:~$ 

```

i do as explain but still can't get it......

You don't need to use sudo and you must leave a space between gedit and /etc.

You can copy and paste the line below to your terminal:
```
gedit /etc/apt/sources.list
```

Alternatively, you can navigate with nautilus (file browser), and open the file. No need to use the terminal.

---

### Post by nainif82 on 2009-12-01
```
zulkarnain@zulkarnain-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Get:1 http://wine.budgetdedicated.com hardy Release.gpg [189B]                               
Hit http://archive.ubuntu.com hardy Release.gpg                                              
Ign http://archive.ubuntu.com hardy/main Translation-en_US                                 
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://ppa.launchpad.net hardy Release.gpg                                             
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US                           
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://ppa.launchpad.net hardy/main Translation-en_US                                  
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US                         
Get:2 http://wine.budgetdedicated.com hardy Release [1016B]                                
Ign http://wine.budgetdedicated.com hardy Release                                            
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US                           
Ign http://archive.ubuntu.com hardy/universe Translation-en_US       
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US     
Hit http://archive.ubuntu.com hardy-updates Release.gpg              
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US   
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://packages.medibuntu.org hardy Release                      
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                
Ign http://wine.budgetdedicated.com hardy/main Packages                                      
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-security Release.gpg             
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US                        
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US                  
Hit http://packages.medibuntu.org hardy/free Packages                                      
Ign http://ppa.launchpad.net hardy/main Packages                     
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US                  
Hit http://archive.ubuntu.com hardy-backports Release.gpg                                  
Hit http://wine.budgetdedicated.com hardy/main Packages                                    
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_US                 
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_US 
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_US
Hit http://packages.medibuntu.org hardy/non-free Packages
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://archive.ubuntu.com hardy Release    
Hit http://archive.ubuntu.com hardy-updates Release                 
Hit http://archive.ubuntu.com hardy-security Release                
Hit http://ppa.launchpad.net hardy/main Packages                    
Hit http://archive.ubuntu.com hardy-backports Release
Hit http://archive.ubuntu.com hardy/main Packages                   
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/universe Sources
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Fetched 191B in 4s (44B/s)
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
zulkarnain@zulkarnain-laptop:~$ 

```

I am already put the code
```
deb http://ppa.launchpad.net/paulburton89/ubuntu hardy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu hardy main
```
into software sources but when i am runnig the terminal to update the error as above.

I put it here
```
W: GPG error: http://wine.budgetdedicated.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
```

What should i do? i need to install galaxium but still can't install it.

---

### Post by Mandred on 2010-01-03
I've been trying to install the -svn but I end up with this error.

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  galaxium-svn: Depends: gstreamer0.10-plugins-farsight (>= 0.12.8)
E: Broken packages

```

Has anybody got a solution?
Thanks in advance.

---

### Post by icyzer on 2010-02-22
Is Galaxium still any good, I just never hear from it again. Can't find any karmic PPA's either. 

Otherwise, and alternative?

---

### Post by TheNessus on 2010-02-22
> **icyzer said:**
> Is Galaxium still any good, I just never hear from it again. Can't find any karmic PPA's either. 

Otherwise, and alternative?
emesene is a nice alternative. 
kopete beats all I think.
galaxium is great though, didn't try to install it on karmic though.

---

### Post by shihkster1015 on 2010-02-23
i was a fan of galaxium for a long time til today. 
Galaxium used to be the only program that can show my yahoo contacts on my hotmail account. But now that pidgin can do that too, i switched over to pidgin.
Pidgin's also light weight program compared to a few others that i used.

---

### Post by kikloo on 2010-04-22
> **atomkarinca said:**
> For future reference, here's how you install it:

Open up your sources list and add the appropriate repository

```
gksudo gedit /etc/apt/sources.list
```

For Gutsy:

```
deb http://ppa.launchpad.net/paulburton89/ubuntu gutsy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu gutsy main
```

For Hardy:

```
deb http://ppa.launchpad.net/paulburton89/ubuntu hardy main
deb-src http://ppa.launchpad.net/paulburton89/ubuntu hardy main
```

then update and install:

```
sudo apt-get update
sudo apt-get install galaxium
```

Hi,

After adding the hardy, when i try to update i get:

```
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E0219167854A3A9
```

Update fails and hence i cannot install it. Anyways I can skip the installation if someone can tell me if this IM supports file transfers in GTalk or not ?

Thanks.

---

### Post by shihkster1015 on 2010-04-24
> **kikloo said:**
> Hi,

After adding the hardy, when i try to update i get:

```
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E0219167854A3A9
```Update fails and hence i cannot install it. Anyways I can skip the installation if someone can tell me if this IM supports file transfers in GTalk or not ?

Thanks.


Go ahead and use keyserver.ubuntu.com
that's where all the keys are

---

### Post by yoncy on 2010-06-05
Did anyone make it works in Ubuntu 10.04. 
When i try to update this errors appears: 

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Fetched 3,803B in 1s (3,447B/s)
W: Failed to fetch [http://ppa.launchpad.net/galaxium/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/galaxium/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ionut/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ionut/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

This happends also on hardy or gutsy deb sources.

---

### Post by MikeDK on 2010-07-20
Hi i was wondering about what happend to galaxium, is there any developing going on on this app? i really liked it when it was new.

kind regards mikedk

---

