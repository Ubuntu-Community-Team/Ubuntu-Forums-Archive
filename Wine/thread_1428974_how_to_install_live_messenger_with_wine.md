---
title: "how to install live messenger with wine?"
date: 2010-03-13
forum: Wine
---

### Post by grobar87 on 2010-03-13
I try to install windows live messenger...but wine not working.I go to 'run aplication with wine' but nothing happens.I use wine 1.1.40.Any other way to install messenger?

---

### Post by Atzu on 2010-03-13
Try this...: [http://www.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html) 

Also why don't you give a try to emesene [http://www.emesene.org/](http://www.emesene.org/) or amsn [http://www.amsn-project.net/](http://www.amsn-project.net/) I believe both are in Ubuntu repos and they look like windows live.

---

### Post by rockerphil on 2010-03-13
have you considered using a native Linux application rather than an app through Wine? i know for a fact that there are at least 2 programs that support MSN messenger. Pidgin and aMSN, these can be installed by either the Add/Remove, Synaptic or via the command line using apt-get.

```
sudo apt-get install pidgin
```

```
sudo apt-get install amsn
```

but if you're intent on running the app through Wine you can always run it through the terminal by using the cd command (works just like the old DOS command) try running this command and see if it's even installed through Wine

```
cd ~/.wine/drive_c/Program\ Files
```

that will navigate you to the directory where all programs are installed in Wine, then run this command to list all folders

```
ls
```

if the messenger is indeed installed then simply cd to the program folder and run the primary .exe file using the wine command. for example

```
wine msn.exe
```

be sure to replace "msn.exe" with the proper executable. hope this info helps,

Phil

---

### Post by sandyd on 2010-03-13
you sure you want to install it when you cant even see what your typing?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8146](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8146)

I would reccomend Kmess, its quite similar to wlm

---

### Post by leveliv on 2010-03-13
That it does, I just say leave msoft software to msoft oses with the exception of office and various games. but things like MSN, they are bloated and better left to just use their protocols with things like Pidgin and even aMSN or "emesene" which is my favourite. Or better yet once you use 10.04 (if you do) Empathy, so it will work with the new MeMenu which is a nice addon.

---

### Post by Teber on 2010-03-13
i'm quite happy using amsn. it gives everything i could want from live messenger, including cute letters in color. as to the website msn live: it works very smoothly in firefox whether running windoze or linux. i fail to see why anyone would want to install the windoze version under linux...

---

### Post by rockerphil on 2010-03-13
most people coming from Windows to Ubuntu/Linux are just getting use to the fact that there is a choice when it comes to software, so it's simply habit to try to install the same apps you used under Windows, and that's why we're here to help them learn that there is an alternative

---

### Post by Crimsonjester on 2010-03-13
OK I am in the same boat I am coming over to Linux, but how do I talk to my contacts on Windows Live Messenger with a Linux program is this possible?? I use Windows Live Messenger for work and my contacts  cannot just switch over to a new I/M program. If I cannot find a way to instant message my work contacts on Windows Live Messenger then I will have to stay over in Windows instead of making the plunge. I appreciate the fact of  why I should use other Instant Messenger programs and that everyone has their preference. This is basically the straw if I can use Ubuntu, I have found every compatible program necessary to do my job except  for windows live messenger...


    Thanks Hobie

---

### Post by qwerty2009 on 2010-03-13
your contacts are not tied to your operating system, there tied to your account(hotmail,msn,live)so they will work from any messenger application.

this is the latest emesene, it has the exact same features as windows live messenger [http://ftp.us.debian.org/debian/pool/main/e/emesene/emesene_1.6-1_all.deb]("http://ftp.us.debian.org/debian/pool/main/e/emesene/emesene_1.6-1_all.deb") 
[IMG]http://www.emesene.org/img/emesene-login.png[/IMG][IMG]http://www.emesene.org/img/emesene-main.png[/IMG][IMG]http://www.emesene.org/img/emesene-conversation.png[/IMG]

---

### Post by dfreer on 2010-03-14
> **Crimsonjester said:**
> OK I am in the same boat I am coming over to Linux, but how do I talk to my contacts on Windows Live Messenger with a Linux program is this possible?? I use Windows Live Messenger for work and my contacts  cannot just switch over to a new I/M program. If I cannot find a way to instant message my work contacts on Windows Live Messenger then I will have to stay over in Windows instead of making the plunge. I appreciate the fact of  why I should use other Instant Messenger programs and that everyone has their preference. This is basically the straw if I can use Ubuntu, I have found every compatible program necessary to do my job except  for windows live messenger...


    Thanks Hobie

Your contacts are stored on a Microsoft server somewhere. When you use a IM program (whether it's Microsoft's Live Messenger or Pidgin or some of the other programs mentioned), you login to their server using your previous username/password. All your contacts will then show up as if nothing happened, no problems at all.

For the record, I'm currently using Pidgin in Windows 7 simply because Pidgin covers a HUGE variety in IM protocols, such as AIM, Jabber, Facebook Chat, Xfire, etc. Doesn't really matter though because my contacts are tied to my username, not to the program itself.

---

### Post by Crimsonjester on 2010-03-14
Complete success... Thank you...


Not only did I transfer all of my work contacts but my friends on a second one..


Thank you very much, Hobie

---

### Post by Tikkyca on 2010-03-14
> **grobar87 said:**
> I try to install windows live messenger...but wine not working.I go to 'run aplication with wine' but nothing happens.I use wine 1.1.40.Any other way to install messenger?

Install emesen for ubuntu it is awsome,also install skipe if you like chatting,are you from Serbia?

---

### Post by grobar87 on 2010-03-14
ok tnx to everyone...:)
i use pidgin right now but i am not very happy...i not recived  all messages :S
(i am from macedonia....pozdrav :D )

---

### Post by sigurnjak on 2010-03-14
I am using Epathy now . It works for my gmail . win live account and facebook . Try it out it is not bad . 
BTW, puno pozdrava is Kanade vama obadvojci ! :p

To  who do not understand , just sending greetings to folks from old country ! :p

---

### Post by cusinmex on 2010-03-14
I use aMSN.

Its the closest thing to Windows Live
and FAR better than Pidgin.

(my opinion)
[http://www.amsn-project.net/download.php]("http://www.amsn-project.net/download.php")

---

### Post by Crimsonjester on 2010-03-15
Which mail will work for Outlook Express? I need all my different email accounts to go to one place. Does Ubuntu have a mail program that will do that???

---

### Post by sigurnjak on 2010-03-15
First i switched from outlook express to Thunderbird , and then copied my profile to Linux Thunderbird  .Afterward i added my gmail and my wifes hot mail and yahoo mail to Thunderbird . So yes there is a such program that can handle multiple email accounts and providers .

---

### Post by Crimsonjester on 2010-03-15
kool good to know .. can i uninstall the empathy mail or whatever its called??

---

### Post by sigurnjak on 2010-03-15
If you mean Evolution , yes you can .

---

### Post by Crimsonjester on 2010-03-15
seweet doing it now and installing tbird..thanks guys

---

### Post by texashold on 2010-03-16
Lets check out this video  [http://www.youtube.com/watch?v=xYLv67CINjA](http://www.youtube.com/watch?v=xYLv67CINjA)

---

### Post by grobar87 on 2010-03-17
tnx to all i solved the problem...
(sigurnjak puno pozdrava!)

---

### Post by Crimsonjester on 2010-03-18
Did you get msn to install with wine or just use Emesene..?

---

### Post by qwerty2009 on 2010-03-18
he must have used emesene, amsn, pigeon, or empathy

even if someone did install the official  wlm you cannot type as you cant see messages or what your writing.

emesene is the closest native wlm client :D

---

### Post by alex.rayu on 2010-03-18
Why dead messengers? Use Emesene - you need no wine for it, only vodka.

---

### Post by Nisal on 2010-03-18
why the hell u need to use msn when there is something like pidgin ?

---

### Post by ale2010 on 2010-03-18
> **Atzu said:**
> Try this...: [http://www.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html) 
 
Also why don't you give a try to emesene [http://www.emesene.org/](http://www.emesene.org/) or amsn [http://www.amsn-project.net/](http://www.amsn-project.net/) I believe both are in Ubuntu repos and they look like windows live.
 
 
I saw the screen shots, i will install Emesene this saturday.  Thanks a lot, the link was very helpful.  Have a nice day ;)

---

