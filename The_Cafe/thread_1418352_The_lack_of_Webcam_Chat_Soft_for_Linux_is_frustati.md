---
title: "The lack of Webcam Chat Soft for Linux is frustating."
date: 2010-02-28
forum: The Cafe
---

### Post by markinf on 2010-02-28
Seriously guys one of the things that I eventually use Windows for is Webcam chat. Even through we have the Webcam working, we dont have any 'decent' application to use it. I did a extensively test on three computers a Desktop (Custom / Extern WC), Netbook (HP-Mini / Internal WC) and Notebook (Toshiba Satellite / Internal WC) ALL with different Webcams models. Let's start the test with the following candidates:

1 - Skype
Well the one that 'works' best is a prop software. Skype for Linux is currently on VERSION 2.1.0.81 while for Windows it's on VERSION 4.2.0.152.
Not only that the Linux version is horribly, most of the times the sound is cutting and the Webcam JUST stops when it wants. TO COMPLETE, the Webcam moves at the coolest 1fpm, 1 frame per minute, it's bizarre. 

2 - Empathy [GTalk only]
The webcam has NEVER worked with me on Empathy, and I'm really seriously. It just don't work. 

3 - Ekiga
This is laughable. Seriously I had to go to the dev IRC channel to get the program to at least 'work'. It seems that they hard coded the size of the data pkg larger than expected, so thats why it's unusable.

4 - AMSN and Emesene
Don't work Period. I have try extensively with different contacts and all failed. All get a black screen.

Conclusion:
Most of the time ppl have said to me that 'Webcam' is irrelevant. That is, they don't want/don't know how to fix the problem and are trying to change something thats REALLY COMMON on the desktop world.

How can I tell my mother that she can't use here webcam on her reunions. How can We expected desktop users to use Linux if we can't handle this basic stuff?

---

### Post by Ubom on 2010-02-28
I just want to ask you one question, if your webcam had not worked in Windows would you have blamed Microsoft?
I doubt it.
Just because these don't work for you doesn't mean they don't work at all, most people have perfect functionality with these apps.
Sorry it doesn't help your problem but perhaps use the support forum for guidance.

---

### Post by markinf on 2010-02-28
Well in all of my three pcs it works 100% on Windows. And in my university all of my colleagues that use Linux none of them have a workable webcam under Linux. So after seeing more than 30+ computer and none of a working webcam soft I can affirm and say that It just doesn't work :P

---

### Post by blueturtl on 2010-02-28
Gotta take the babby to bed and read her a bedtime story. After that I will return to troubleshoot your problem. :)

I use Ekiga and it works just swell.

---

### Post by Ubom on 2010-02-28
> **markinf said:**
> Well in all of my three pcs it works 100% on Windows. And in my university all of my colleagues that use Linux none of them have a workable webcam under Linux. So after seeing more than 30+ computer and none of a working webcam soft I can affirm and say that It just doesn't work :P

Well before you give up on Linux I think I should add that I have:
Desktop with a Microsoft Lifecam cinema (worked out of the box with 720p recording and microphone).
Acer Aspire one, 9inch model - worked out of the box.
Macbook Pro - Didn't work out of the box but using a guide eventually managed to get it working.

If you are having too many problems just go with a Lifecam Cinema, very good and works well.
What model webcam do you have at the moment? What version of Ubuntu are you running?

---

### Post by spikyjt on 2010-02-28
Ekiga works for me too, but I have had trouble with codecs. It all depends on what the client at the other end can support. If its Ekiga to Ekiga with the same codecs at each end (most of the decent ones aren't available in ffmpeg since Jaunty) then fine, otherwise you may have trouble. But make sure your webcam is definitely working happily in linux, before blaming the application software. Again Ekiga should allow you to see a preview of your webcam, once it is set up (the wizard is very comprehensive and easy to follow). Oh and the Ekiga package for Karmic definitely works out of the box.

---

### Post by bark50 on 2010-02-28
For Yahoo IM webchat, Gyache works for me:  [http://ubuntuforums.org/showthread.php?t=773802]("http://ubuntuforums.org/showthread.php?t=773802")

---

### Post by blueturtl on 2010-02-28
Back. Now is the problem specifically about the webcam, or about the chat software?

If you have a problem with your camera post detailed info about the camera and your system (if we're talking about a portable computer).

If the problem is not with the camera (camera works, but you just can't initiate calls) please post more info on your network set up and if possible, the call recipients network set up.

The fact that your post is about the applications implies that the web cam is working, but you are having trouble making it work on the listed client programs.

---

### Post by Nevon on 2010-02-28
Works just fine for me. At least in aMSN. I haven't tried any other ones.

---

### Post by Mr. Picklesworth on 2010-02-28
> **markinf said:**
> 2 - Empathy [GTalk only]
The webcam has NEVER worked with me on Empathy, and I'm really seriously. It just don't work. 

If you're okay breaking the messaging menu integration, the latest Empathy (there's a PPA for latest Telepathy and Empathy) which will ship in Lucid does a way better job with webcam stuff than what is in Karmic. It even does it for MSN, thanks to the new [Papyon]("http://telepathy.freedesktop.org/wiki/Papyon") library :)

As for protocol, the best one for webcam use, if you can convince everyone you know, is going to be XMPP through Jabber.org. (Google Talk does some stuff a tad differently which can cause issues, and Facebook doesn't do webcam stuff).

---

### Post by sudoer541 on 2010-02-28
> **markinf said:**
> Seriously guys one of the things that I eventually use Windows for is Webcam chat. Even through we have the Webcam working, we dont have any 'decent' application to use it. I did a extensively test on three computers a Desktop (Custom / Extern WC), Netbook (HP-Mini / Internal WC) and Notebook (Toshiba Satellite / Internal WC) ALL with different Webcams models. Let's start the test with the following candidates:

1 - Skype
Well the one that 'works' best is a prop software. Skype for Linux is currently on VERSION 2.1.0.81 while for Windows it's on VERSION 4.2.0.152.
Not only that the Linux version is horribly, most of the times the sound is cutting and the Webcam JUST stops when it wants. TO COMPLETE, the Webcam moves at the coolest 1fpm, 1 frame per minute, it's bizarre. 

2 - Empathy [GTalk only]
The webcam has NEVER worked with me on Empathy, and I'm really seriously. It just don't work. 

3 - Ekiga
This is laughable. Seriously I had to go to the dev IRC channel to get the program to at least 'work'. It seems that they hard coded the size of the data pkg larger than expected, so thats why it's unusable.

4 - AMSN and Emesene
Don't work Period. I have try extensively with different contacts and all failed. All get a black screen.

Conclusion:
Most of the time ppl have said to me that 'Webcam' is irrelevant. That is, they don't want/don't know how to fix the problem and are trying to change something thats REALLY COMMON on the desktop world.

How can I tell my mother that she can't use here webcam on her reunions. How can We expected desktop users to use Linux if we can't handle this basic stuff?


I have to agree with you 100% buddy!
I've got the same problem and I cant use webcam for my MSN contacts on empathy or any other communication app.
Seriously if Linux has tons of programmers, why dont they ever create a good app for MSN users (webcams)?

---

### Post by t0p on 2010-02-28
> **sudoer541 said:**
> 
Seriously if Linux has tons of programmers, why dont they ever create a good app for MSN users (webcams)?

Because they're creating other stuff of course.  Duh!  :p

---

### Post by juancarlospaco on 2010-02-28
Since you have **shared desktop**, _doesnt matter if the webcam dont work_, 
just bring up the preferred webcam program *(locally)* and share your desktop,
you see the webcam locally, your contact see the same as you see.
*Just think different way to use it.*

BTW webcam works perfect on Empathy.

---

### Post by blueturtl on 2010-03-01
I thought this was one of *those* flaming posts that are supposed to trigger the help from the community by pissing everybody off.

I am not pissed, but still ready to help if the OP still wishes to configure Ekiga.

---

### Post by Keyper7 on 2010-03-01
> **markinf said:**
> Skype for Linux is currently on VERSION 2.1.0.81 while for Windows it's on VERSION 4.2.0.152. Not only that the Linux version is horribly, (...)

Slightly off topic, but am I the only one who actually *likes* the Skype Linux interface? I find the Windows version horribly bloated, like the current Windows Media Player compared to good old Media Player Classic. Whenever I open it, I feel like RealPlayer/RealJukebox rose from the grave to haunt the 21st century. Furthermore, Skype for Windows *pretends* to integrate with Aero but in the end looks quite alien, while Skype for Linux looks satisfactorily native either on Qt or Gtk.

---

### Post by Boondoklife on 2010-03-01
I use skype on a daily basis and it works out great for me. I wish skype would open up their code a little bit to allow a tighter integration into another app though, kinda annoying having to have skype and another chat app open at the same time.

---

### Post by aysiu on 2010-03-01
I've done a *lot* of Skyping using Linux, Windows, and Mac, and I can tell you straight-up that things can just be buggy. I haven't found Linux to be particularly buggy. In fact (this is anecdotal, of course), I've had a lot more freeze-ups or mismatched sound/video using Windows than using Linux or Mac.

I also have an HP Mini, by the way. The only real consistent problem I've had is that the webcam on the HP Mini displays quite dimly if I don't shine a bright light or chat with some sunlight streaming through the window. I also have a 0.3 megapixel camera, so the resolution isn't high quality. Neither of those problems has to do with Linux, though.

---

### Post by RichardLinx on 2010-03-01
If it's any consolation Kmess 2.1 is going to be focused on multimedia (ie, Voice and Video Chat).

Also when I was using Linux I never had a problem getting my webcam to work.

---

### Post by rajeev1204 on 2010-03-01
> **blueturtl said:**
> I thought this was one of *those* flaming posts that are supposed to trigger the help from the community by pissing everybody off.

I am not pissed, but still ready to help if the OP still wishes to configure Ekiga.


Thats the beauty of this forum and its members, it takes a negative post and changes it gently into a hand holding support session.

Of course, the OP never used bad language and his post is only really showing  his disappointment , and we got the message.: ) So we all turn up to help.

---

### Post by Neezer on 2010-03-01
I have been in the same boat as the OPer. I use skype, and had it working in 9.04. I had to buy a USB camera and use the audio on the USB camera and the built in video on my laptop...So I guess sound has been my problem with the app, but viedo as well. I have tried so many times to get the audio working I don't know what to do anymore.

I don't know much about skype, but it is incredibly lacking in this department...it is odd to me because it worked for me flawlessly in windows. I'm moving to germany in 4 months and I'd hate to have to put windows on my machine so that I can skype with friends and family while i'm in germany for 6 months....It is quite infuriating, but it is also free.

---

### Post by jwbrase on 2010-03-01
> **Neezer said:**
> I have been in the same boat as the OPer. I use skype, and had it working in 9.04. I had to buy a USB camera and use the audio on the USB camera and the built in video on my laptop...So I guess sound has been my problem with the app, but viedo as well. I have tried so many times to get the audio working I don't know what to do anymore.

I don't know much about skype, but it is incredibly lacking in this department...it is odd to me because it worked for me flawlessly in windows. I'm moving to germany in 4 months and I'd hate to have to put windows on my machine so that I can skype with friends and family while i'm in germany for 6 months....It is quite infuriating, but it is also free.

Coincidence: I myself am in Germany on an exchange trip.

I'm still using 9.04 myself (I was in Germany by the time 9.10 came out, and having had I bad experience with upgrading *to* Jaunty on another machine, I decided not to do any upgrades till I get home (Plus, 10.04 will be the next LTS)). 

Skype works fine for me on Jaunty, and is a very, very convenient way to call back to the states. I did have to fiddle a bit to get the sound working, and I haven't gotten it working with the headphones I have here with me yet (partially for lack of trying, I think), but otherwise, it's great.

---

### Post by blueturtl on 2010-03-01
The hardest part about standard SIP phones is that if you have a crappy router, the calls won't go thru or you get audio without the video or stuff like that.

But people don't know that so they knock the software. I insisted on my parents using Ekiga (or some standards compliant phone app) because I knew that I wouldn't want to be at the mercy of Skype for Linux.

At first it really didn't work very well at all. Well turns out my router could be configured to work half-decent. Theirs had good features (port range triggering) but was pretty crash prone.

After switching devices things now work like a charm. Just something to keep in mind. Also it doesn't matter what OS or hardware my call pals are running because there are multiple SIP compliant phone apps for Linux, Mac OS and Windows.

The web cam problem in Linux was due to lack of standards (had to have an expensive Firewire cam in the early days) but now they've finally got a standard for USB video too (UVC). All in all I'm surprised how many web cams already work with no configuration at all.

/endLecture

---

### Post by samh785 on 2010-03-01
I use skype very often and suffer none of the problems that you have pointed out.

---

### Post by Regenweald on 2010-03-01
> **markinf said:**
> Seriously guys one of the things that I eventually use Windows for is Webcam chat. Even through we have the Webcam working, we dont have any 'decent' application to use it. I did a extensively test on three computers a Desktop (Custom / Extern WC), Netbook (HP-Mini / Internal WC) and Notebook (Toshiba Satellite / Internal WC) ALL with different Webcams models. Let's start the test with the following candidates:

1 - Skype
Well the one that 'works' best is a prop software. Skype for Linux is currently on VERSION 2.1.0.81 while for Windows it's on VERSION 4.2.0.152.
Not only that the Linux version is horribly, most of the times the sound is cutting and the Webcam JUST stops when it wants. TO COMPLETE, the Webcam moves at the coolest 1fpm, 1 frame per minute, it's bizarre. 

2 - Empathy [GTalk only]
The webcam has NEVER worked with me on Empathy, and I'm really seriously. It just don't work. 

3 - Ekiga
This is laughable. Seriously I had to go to the dev IRC channel to get the program to at least 'work'. It seems that they hard coded the size of the data pkg larger than expected, so thats why it's unusable.

4 - AMSN and Emesene
Don't work Period. I have try extensively with different contacts and all failed. All get a black screen.

Conclusion:
Most of the time ppl have said to me that 'Webcam' is irrelevant. That is, they don't want/don't know how to fix the problem and are trying to change something thats REALLY COMMON on the desktop world.

How can I tell my mother that she can't use here webcam on her reunions. How can We expected desktop users to use Linux if we can't handle this basic stuff?

Hardware manufacturers creating drivers for their product for a specific platform is a very simple concept. Try it on for size.


> **sudoer541 said:**
> I have to agree with you 100% buddy!
I've got the same problem and I cant use webcam for my MSN contacts on empathy or any other communication app.
Seriously if Linux has tons of programmers, why dont they ever create a good app for MSN users (webcams)?

This is just special.

---

### Post by RichardLinx on 2010-03-01
@OP: Try this: 
```
sudo apt-get install cheese
```
The first time I used Ubuntu (7.10) my webcam wouldn't work for the life of me, whatever cheese installed, it fixed my problem.

---

### Post by Johnsie on 2010-03-01
I've found that Skype is the only mainstream application that works well for cross platform video chat. There's a few others out there but they aren't mainstream and the quality of the software is a bit lacking. It seems a bit silly asking 20 people to change their software so they can talk to you when in reality you could change your software and save them the effort. Video messaging is the main reason I went back to Windows after 3 years exclusively on Linux. Sadly there has not been alot of progress on this front since 2005. I still use Linux for server stuff and some non-multimedia stuff but I find that Windows still has the edge wehn it comes to multimedia and video chat. If this issue was dealt with and the sound system issues resolved then I would be more than happy to use Ubuntu as my main OS again.

---

### Post by DutchLoki on 2010-03-12
I'm happy with pidgin and ekiga.

But i've read somewhere its possible to install Virtual box, install your preferred operating system (ehum xp, win 7, or something) then install skype... should work.

Not tested myself, just a suggestion... don't blame the dutch guy if its not working ;)

---

### Post by katie-xx on 2010-03-12
Web Cams are fine provided:.............................

1:   Teenage boys are not allowed to use them for unwanted approaches to girls.

2:  Perverts are not allowed to see other people's cams

All requests and pleadings to take your top off or similar are automatically filtered out and maybe routed to the police station by the controller software.

Kate

---

### Post by Boondoklife on 2010-03-12
> **katie-xx said:**
> Web Cams are fine provided:.............................

1:   Teenage boys are not allowed to use them for unwanted approaches to girls.

2:  Perverts are not allowed to see other people's cams

All requests and pleadings to take your top off or similar are automatically filtered out and maybe routed to the police station by the controller software.

Kate

Heh I like to sit in front of my laptop naked... So woe be to the person that decides to tap into mine!

---

### Post by samh785 on 2010-03-12
> **Boondoklife said:**
> Heh I like to sit in front of my laptop naked... So woe be to the person that decides to tap into mine!
lmfao

---

### Post by kuvanito on 2010-03-12
markinf came here for a reason and frustration and his post got carried out
many of you here in this forum have been Ubuntu users for sometime and perhaps most of you are not into the windows world anymore or not as much but really markinf as myself are windows users trying to come onboard and must of our contacts are windows users and IT IS TRUE! there is not a single app in Linux (Ubuntu) that works well with MSN protocol,I myself have three different cams incluiding the lifecam and it does not work what so ever with any linux app to videochat or voicechat with MSN contacts in windows,that is why his frustration and mine and so many millions.That is why it's hard to convince people to even take a look at Ubuntu Linux Based.

Ekiga,aMSN,Skype,Emesene and others may work well for you if your partner is using the same app or runing the same OS but not for the rest of us 95% of computer users,get it now?
Linux Must come to this term if it wants to be more popular.Don't get me wrong I love Ubuntu,been using it for 6 months now,it's wonderful when you don't have to worry about viruses and pop ups and all the crap that windows brings but Video/Voice Chat is a MUST (MSN and Yahoo)

---

### Post by katie-xx on 2010-03-12
> **kuvanito said:**
> 
Linux Must come to this term if it wants to be more popular.Don't get me wrong I love Ubuntu,been using it for 6 months now,it's wonderful when you don't have to worry about viruses and pop ups and all the crap that windows brings but Video/Voice Chat is a MUST (MSN and Yahoo)

Linux has nothing to do with it though :)

If people want to develop applications for Linux then no one is stopping them.

Skype, incidentally, works fine on my machine


Kate

---

### Post by sudoer541 on 2010-03-12
> **kuvanito said:**
> markinf came here for a reason and frustration and his post got carried out
many of you here in this forum have been Ubuntu users for sometime and perhaps most of you are not into the windows world anymore or not as much but really markinf as myself are windows users trying to come onboard and must of our contacts are windows users and IT IS TRUE! there is not a single app in Linux (Ubuntu) that works well with MSN protocol,I myself have three different cams incluiding the lifecam and it does not work what so ever with any linux app to videochat or voicechat with MSN contacts in windows,that is why his frustration and mine and so many millions.That is why it's hard to convince people to even take a look at Ubuntu Linux Based.

Ekiga,aMSN,Skype,Emesene and others may work well for you if your partner is using the same app or runing the same OS but not for the rest of us 95% of computer users,get it now?
Linux Must come to this term if it wants to be more popular.Don't get me wrong I love Ubuntu,been using it for 6 months now,it's wonderful when you don't have to worry about viruses and pop ups and all the crap that windows brings but Video/Voice Chat is a MUST (MSN and Yahoo)

I have high hopes for lucid. As someone said earlier telepathy would be integrated with empathy and it would work better than karmic koala. I hope this is possible.

---

### Post by aysiu on 2010-03-12
> **kuvanito said:**
> there is not a single app in Linux (Ubuntu) that works well with MSN protocol Do you honestly believe it's because Microsoft has said to the Linux developers, "Here is exactly how to work with our protocol. We want to help you develop a Linux-native application to work with all the features of MSN chat" and the Linux developers responded back "Screw you. No Linux user would want that"? Is that the narrative you're constructing in your head.

I can assure you Microsoft has done no such thing. They are notorious for not playing nice. Plenty of closed source companies play nice with Linux (Opera, Google, DropBox). Microsoft is not one of them. If people open their code or open their specifications or use open formats, Linux does just fine.

Imagine you have a eight-year-old daughter. A popular kid in class is throwing a party, but in order to find where the party is, you have to know what the secret code word is. She has a different secret code word for each person in the class, and she tells each code work to those invited. She doesn't tell your daughter, though. Suddenly, when your daughter cries because she wasn't invited to so-and-so's party, you blame her and say "Look, get with the program. You can't expect people to be your friend if you don't even go to the party the popular girl throws."

> Ekiga,aMSN,Skype,Emesene and others may work well for you if your partner is using the same app or runing the same OS but not for the rest of us 95% of computer users,get it now? And until recently my wife couldn't stream Netflix on her Mac. She can't play all the computer games she wants on her Mac (so she uses a PS3 and Wii). There's no Microsoft OneNote for Macs or AutoCAD for Macs. Fortunately, for her, she has no use for OneNote or AutoCAD.

So if you want Windows software, guess what--you use Windows. I'm not trying to be mean. I'm being extremely practical here. You do what you can. If you use Windows-only software, it makes sense to use Windows. If you don't, you have the freedom to use Mac OS X or Linux.

Perhaps instead of blaming your daughter for not inviting herself to the secret party, you should tell her to throw her own parties... or blame the popular girl for not inviting her.

---

### Post by kuvanito on 2010-03-12
> **aysiu said:**
> Do you honestly believe it's because Microsoft has said to the Linux developers, "Here is exactly how to work with our protocol. We want to help you develop a Linux-native application to work with all the features of MSN chat" and the Linux developers responded back "Screw you. No Linux user would want that"? Is that the narrative you're constructing in your head.

I can assure you Microsoft has done no such thing. They are notorious for not playing nice. Plenty of closed source companies play nice with Linux (Opera, Google, DropBox). Microsoft is not one of them. If people open their code or open their specifications or use open formats, Linux does just fine.

well,then linux should create something that works video and audio chat just for linux,as far as I can see Empathy or Pigin are just protocol grabbers (robbers) should I say.Perhaps I would love to see something like Vibuntu and create my own account and chat with my contacts using Ubuntu-Linux in Vibuntu with Video and voice chat but that does not exist yet...It is the lack of apps that we are talking about.

---

### Post by leandromartinez98 on 2010-03-12
You are lucky to have voice chat. I was never able to have decent skype/empathy voice or whatever working in any of my ubuntu machines. And the problem is on the sound architecture, since mostly the voce recording with the sound recorder is very poor or needs a fine-tunning-computer-specific input sound volume every time. And there is echo...

---

### Post by leandromartinez98 on 2010-03-12
> **Johnsie said:**
> ... Linux. Sadly there has not been alot of progress on this front since 2005....

This is true. I think Canonical has a focus problem there. The problems with chat/video are related to drivers for the webcams and with the sound architecture, which are still underdeveloped for Linux. The sound architecture is been improved by the ongoing work on pulseaudio but guess, this is being financed by RedHat. The driver development probably as well, or by someone else. This facts and Canonical not putting many efforts to make OpenOffice better is what makes me think that there is an important focus problem. Their Linux-desktop goal needs OpenOffice and needs good multimedia support, not new icons, the old ones are not that ugly.

Edit: also I guess it is much harder and expensive to find a sound architecture developer than a designer to draw new icons.

---

### Post by DutchLoki on 2010-03-13
> **kuvanito said:**
> well,then linux should create something that works video and audio chat just for linux,as far as I can see Empathy or Pigin are just protocol grabbers (robbers) should I say.Perhaps I would love to see something like Vibuntu and create my own account and chat with my contacts using Ubuntu-Linux in Vibuntu with Video and voice chat but that does not exist yet...It is the lack of apps that we are talking about.

Your not getting it... both Empathy and pidgin are opensource and support open standards. There's no need for another app.

The problem is the kernel and some distro's (including my favorite, ubuntu (and slackware)). The audio and video stuff is a bit hackisch... the good news is, its getting there... but it will take more than a little time.

At this moment your(generally meant, don't know you) computer skills just need te be a bit more than people are used to on Windows... Not good for linux but still very true.

---

### Post by gradinaruvasile on 2010-03-13
I use Skype on Linux and my family does too - 6 computers, with Ubuntu 9.10, 8.10, Debian Testing on them. All work perfectly. The webcams we have DONT WORK ON WINDOWS WITH THEIR OWN DRIVERS :lolflag: but work on Linux... 

I have used it with Linux, Windows and Mac on the other side its perfectly compatible, everything works fine (webcams, desktop sharing file transfer etc), the sound quality is the best i have heard.
And on some boxes is ALSA, on others PulseAudio, it works perfectly with both.

Anyway, the idea is to set up your voice and video BEFORE USING any video/voice app.

Sound:

With Ubuntu 9.10 its simple - just right-click on the volume icon, select sound properties, go to the input tab and tap the microphone, if there is any sound input you will see. If there are problems, thare is alsamixer in terminal.

Video:

press alt+f2, type: gstreamer-properties, go to the video tab and selet the webcam, press test. If it works and doesnt work in a program, launch that program this way:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so programname

I have to do this for Skype and Pidgin to use correctly my gspca webcam.

Other than Skype, i tested Pidgin with voice/video, that too worked well. 

The trick in Pidgin was to set the video source EXPLICITLY to something - if there wasnt webcam, the "test input" had to be set manually. Otherwise the webcam of course.

---

### Post by Jarmen_Deffs on 2010-03-13
I use Skype video chat daily, without any trouble at all...

---

### Post by kaldor on 2010-03-13
Built-in webcam works fine on mine. Smooth and clear.

My girlfriend's logitech works great too. 

I never had any problems with cams on any computer.

---

### Post by themarker0 on 2010-03-13
Was i the only one that had to change the router a bit to allow webcams?

---

### Post by quinnten83 on 2010-03-13
> **kuvanito said:**
> markinf came here for a reason and frustration and his post got carried out
many of you here in this forum have been Ubuntu users for sometime and perhaps most of you are not into the windows world anymore or not as much but really markinf as myself are windows users trying to come onboard and must of our contacts are windows users and IT IS TRUE! there is not a single app in Linux (Ubuntu) that works well with MSN protocol,I myself have three different cams incluiding the lifecam and it does not work what so ever with any linux app to videochat or voicechat with MSN contacts in windows,that is why his frustration and mine and so many millions.That is why it's hard to convince people to even take a look at Ubuntu Linux Based.

Ekiga,aMSN,Skype,Emesene and others may work well for you if your partner is using the same app or runing the same OS but not for the rest of us 95% of computer users,get it now?
Linux Must come to this term if it wants to be more popular.Don't get me wrong I love Ubuntu,been using it for 6 months now,it's wonderful when you don't have to worry about viruses and pop ups and all the crap that windows brings but Video/Voice Chat is a MUST (MSN and Yahoo)

Actually amsn was working a dream for me until MS changed the live chat protocol. Since then it hasn't worked the way it should. But it seems if i request a video conference instead of sending or receiving webcam it works.
The only reason I stick with aMSN is because it can log your webcam sessions.

you know, I find it hard to believe that all windows users will not give linux a chance simply because they can't chat naked with each other on cam.

---

### Post by quinnten83 on 2010-03-13
> **themarker0 said:**
> Was i the only one that had to change the router a bit to allow webcams?

If you use aMSN you have to do this.

---

### Post by Warpnow on 2010-03-13
In my experience the problem isn't bad applications but bad drivers.

---

### Post by xx58 on 2010-03-13
:rolleyes:Amsn - works
   GYache (yahoo) - works good
   Skype - like charm

---

### Post by sudoer541 on 2010-03-13
what about if you dont have a cam and others do, will it work?
I have friends and family who have cams and they send me invitations but it never works.
DO I have to have a cam to see them as well?

---

### Post by toupeiro on 2010-03-13
I am using a logitech quick cam Ultra Vision and have been since 6.x or 7.x and it works just fine.  As soon as skype video for linux was available, it worked on day 1.  Echoing others, I think this is less of an ubuntu problem for supporting webcams and more a problem with *your* particular webcam.

---

### Post by mikeize on 2010-05-10
> **gradinaruvasile said:**
> 
Video:

press alt+f2, type: gstreamer-properties, go to the video tab and selet the webcam, press test. If it works and doesnt work in a program, launch that program this way:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so programname

I have to do this for Skype and Pidgin to use correctly my gspca webcam.

Other than Skype, i tested Pidgin with voice/video, that too worked well. 

The trick in Pidgin was to set the video source EXPLICITLY to something - if there wasnt webcam, the "test input" had to be set manually. Otherwise the webcam of course.

I can't thank you enough for this post!  I have the MS lifecam cinema (it was a gift!), and I could *only* get it to work with Cheese, but NO chat programs.  I did the test you recommended, set the latest driver, and then figured out how to make it work with Pidgin!  I don't know why none of my chat programs autoconfigured themselves correctly, since ubuntu sees the device, and Cheese can use it... but I don't care now that I have it working!  Thanks so much for this simple information, that has eluded me for so long.

---

### Post by SubCool on 2010-09-20
I have been trying to manage this very part time. And i am with the noobs. Having webcam support would be nice, But there are practically NO software that can work with windows or MAC. Web Chat is HUGE- howcome this is soo hard to get working? 
Skype works. Kinda Yucky vid quality.
Ekiga? ill get it to work i guess.
Pidgin, ugh- ill try again another day.
Gyache? guess ihave to manually DL it..

We got a couple more to work from. Thats IT!?!?!?

Aim webcam STILL hard to do.
Yahoo webcam, i guess i have to push for GYache?
MSN? - i dont use it, but seriously #1 chat for the world, and we are having issues?

oovoo?
What other webbased chat agent are there even out there? That WORK?

What is a VERY GOOD DEPENDABLE Software so that we can SImply WEBCAM with people from WIndows, or MAC!?!?!?

You guys are pretty and all, but i wanna talk to GIRLS!

If you know of a software or a practice that is normal? LET US KNOW!

---

### Post by cprofitt on 2010-09-20
> **SubCool said:**
> I have been trying to manage this very part time.  And i am with the noobs. Having webcam support would be nice, But there  are practically NO software that can work with windows or MAC. Web Chat  is HUGE- howcome this is soo hard to get working? 
Skype works. Kinda Yucky vid quality.
Ekiga? ill get it to work i guess.
Pidgin, ugh- ill try again another day.
Gyache? guess ihave to manually DL it..

We got a couple more to work from. Thats IT!?!?!?

Aim webcam STILL hard to do.
Yahoo webcam, i guess i have to push for GYache?
MSN? - i dont use it, but seriously #1 chat for the world, and we are having issues?

oovoo?
What other webbased chat agent are there even out there? That WORK?

What is a VERY GOOD DEPENDABLE Software so that we can SImply WEBCAM with people from WIndows, or MAC!?!?!?

You guys are pretty and all, but i wanna talk to GIRLS!

If you know of a software or a practice that is normal? LET US KNOW!

What model of camera do you have, what version of Ubuntu?

---

### Post by manny43 on 2010-10-24
I use an old Logitech Pro 5000 and the only thing i had to do in order to work with Cheese was change
resolution to 352x288 that was it.No problems with other apps like Ekiga,Empathy.

---

### Post by cariboo on 2010-10-24
I have zero problems with any of the webcam enabled programs available in the repositories. Where I do have problems, is with MSN, as amsn doesn't work with the latest Windows version, I have the same problem in XP. 

Windows 7/Logitech doesn't support my Logitch Quickcam Messanger anymore, where it works perfectly with Maverick. The only thing I had to do was set pulsaudio to use the builtin microphone.

The builtin webcam/microphone works out of the box on my Compaq Mini 110. 

The other complaint I have is that Skype needs to be updated, even though it is beta, the interface is just plain crummy and not intuitive at all.

---

