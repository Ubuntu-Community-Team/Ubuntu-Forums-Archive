---
title: "Video call in Linux"
date: 2006-12-05
forum: The Cafe
---

### Post by topgi on 2006-12-05
Hello Guys,
few month ago I convinced my boss to move from windows to Ubuntu. He was so happy to see that he can get rid of virus, worm, costly software, piracy and so on.
BUT, he needs to do video call. His kids want to see the Grandparents. They use windows, so we need a IP phone working in Linux and Windows

No problem, I said, use Openwengo! OK no way, it simply doesn't work in a PC to PC communication, the line drop after few minutes. Beside that there are a lot of problem in setting up the audio and the connection itself.
No problem, I said, use Ekiga! OK no way, the audio sucks, sometimes it work, sometimes not and on the windows side they have to use Netmeeting. Not always works flawlessly and connection drop easily.

The only solution we could find is to use Skype for audio (it works very well) and use a different application for Video like aMSN or Ekiga itself. The problem is now the Grandparent, how to explain that they need 2 application to do something that in windows can be done with one software.

How can I promote Ubuntu to friends and relative if it isn't possible to perform a simple task like a video call ?

---

### Post by seshomaru samma on 2006-12-05
I have no answer for you.
I feel the same.....
Next month I'm switching my mom's Pc to Ubuntu , she needs it mostly for skype and to watch pictures of my son I send her.
I will have to set both aMSN and Skype to have a successful video/audio conversation.
Ultimately after one year of using Linux , I feel that even though it is a superior OS to Windows ,many of its applications are inferior.

---

### Post by kvonb on 2006-12-05
Try Gyachi, it is a messenger which uses the Yahoo protocol so all you need is a free Yahoo account:

[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)

It has both webcam and voice chat, although you will need a compatible webcam, see this site:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

Rgds, KEv :)

---

### Post by Brunellus on 2006-12-05
> **seshomaru samma said:**
> I have no answer for you.
I feel the same.....
Next month I'm switching my mom's Pc to Ubuntu , she needs it mostly for skype and to watch pictures of my son I send her.
I will have to set both aMSN and Skype to have a successful video/audio conversation.
Ultimately after one year of using Linux , I feel that even though it is a superior OS to Windows ,many of its applications are inferior.
you should be aware, of course, that current versions of Skype for Linux do not support video chat. 

This is a major irritant in our family; my mother has to boot into Windows (her less-preferred OS) to video chat.

---

### Post by Turtle.net on 2006-12-05
You can also give qnext a try (java application so OS independent) and supports video, audio, chat, file sharing, photos sharing (organized as albums).
Its a very nice piece of software.

---

### Post by seshomaru samma on 2006-12-06
I tried qnext and must admit that it looks very nice but:
it doesnt support Chinese

---

### Post by styven on 2006-12-06
Can anyone guide me how to install qnext, it is a tar.bz.

Steve

---

### Post by topgi on 2006-12-06
Just untar in a directory and run ./qnext.

---

### Post by styven on 2006-12-06
Thanks for hat , tried it no go.
I have tried other commands and get the following..............

Setting up build-essential (11.1) ...
styven@styven:~$ cd qnext
styven@styven:~/qnext$ ./congigure
bash: ./congigure: No such file or directory
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory
styven@styven:~/qnext$ make
make: *** No targets specified and no makefile found. Stop.
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory
styven@styven:~/qnext$ sudo make install
make: *** No rule to make target `install'. Stop.
styven@styven:~/qnext$ ./qnext
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory

Where am i going wrong?

Steve

---

### Post by patrick295767 on 2006-12-06
> **topgi said:**
> Hello Guys,
few month ago I convinced my boss to move from windows to Ubuntu. He was so happy to see that he can get rid of virus, worm, costly software, piracy and so on.
BUT, he needs to do video call. His kids want to see the Grandparents. They use windows, so we need a IP phone working in Linux and Windows

No problem, I said, use Openwengo! OK no way, it simply doesn't work in a PC to PC communication, the line drop after few minutes. Beside that there are a lot of problem in setting up the audio and the connection itself.
No problem, I said, use Ekiga! OK no way, the audio sucks, sometimes it work, sometimes not and on the windows side they have to use Netmeeting. Not always works flawlessly and connection drop easily.

The only solution we could find is to use Skype for audio (it works very well) and use a different application for Video like aMSN or Ekiga itself. The problem is now the Grandparent, how to explain that they need 2 application to do something that in windows can be done with one software.

How can I promote Ubuntu to friends and relative if it isn't possible to perform a simple task like a video call ?

I have right now teh exact same problem

u can use : skype + amsn

but there is thsi way:

skype + internet webpage that you refresh
you export ur webcam on this page

they have skype + interenet explorer and can see u
but to see them; u need kopete or amsn 

shiity isnt it 

damn skype development

sometimes; we could be awaiting these chineese that cracked maybe the skype stream

---

### Post by arnieboy on 2006-12-06
Voice chat on GyachI works only in chat rooms. I have not been able to successfully use it in one-on-one chat or in conferences (one-to-one  voice chat does not work at all). The people helping me test it were using the latest version of Yahoo Messenger at the time of writing (v8.5).
Receiving webcams works just fine. Sending webcams (for supported webcams)is a little flaky. Webcam starts up just fine but somehow when an invitation to view webcam is sent, the user cannot see the webcam and he/she does not get added to the list of users viewing my webcam. Other users might have had better experiences with GyachI and it would nice if they share the same.

---

### Post by patrick295767 on 2006-12-06
It is really amazing how slow the skype development for linux can be

That s rather curious no ? for such money they can make.

I hoep that they will react and develop a bit faster
[http://forum.skype.com/index.php?showtopic=71046](http://forum.skype.com/index.php?showtopic=71046)

---

### Post by patrick295767 on 2006-12-06
this can be interesting for you:


VideoLinux: Post your script Solutions for sharing your webcam !, scripts scripts scripts scripts scripts
[http://forum.skype.com/index.php?act=ST&f=18&t=71049&st=0#entry328117](http://forum.skype.com/index.php?act=ST&f=18&t=71049&st=0#entry328117)

---

### Post by kvonb on 2006-12-06
SOLVED:

[http://openwengo.com/index.php/mp_download_wp_lin](http://openwengo.com/index.php/mp_download_wp_lin)

I installed WengoPhone and actually bought 10euros credit last year on my Windows partition, I was wondering recently why I did this as I never used it!

It turns out that it's because it does actually support video calls!

Give that a try and see, my webcam doesn't work in Ubuntu hence I never even tried it :rolleyes:.

Please let me know if it works with your webcams.

Kev :)

PS: The install instructions are on the download page, and make sure you download the 15meg BINARY!!

---

### Post by Turtle.net on 2006-12-06
To install qnext you just have to follow the guidelines on their web site [http://qnext.com](http://qnext.com)
> bunzip2 qnextsetup.tar.bz2
						tar -xf qnextsetup.tar
						cd qnext
						./qnext


There is no ./configure ...

---

### Post by seshomaru samma on 2006-12-06
> **styven said:**
> Thanks for hat , tried it no go.
I have tried other commands and get the following..............

Setting up build-essential (11.1) ...
styven@styven:~$ cd qnext
styven@styven:~/qnext$ ./congigure
bash: ./congigure: No such file or directory
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory
styven@styven:~/qnext$ make
make: *** No targets specified and no makefile found. Stop.
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory
styven@styven:~/qnext$ sudo make install
make: *** No rule to make target `install'. Stop.
styven@styven:~/qnext$ ./qnext
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory

Where am i going wrong?

Steve
no need to ./configure
you can do it all graphically
by clicking on the downloaded file then look in the untared directory for a ./qnext file. click on it and you are set....

i didn't mange to do a video conference with it(but I was on Suse I will try with Ubuntu later...)

---

### Post by rsambuca on 2006-12-07
I hate to admit it, but as much as I like open source ubuntu, I can not find any solution to videoconferencing that even comes close to what is available in XP.  The only reason I still keep XP on my computer is for video conferencing.  We use Sightspeed so my daughter can talk and see her Grandparents across the ocean virtually every day.

While Sightspeed is a non-opensource solution, it works, and the video quality is much better than any other program we have tried.  I have tried many different linux to XP methods, but nothing comes close.  Keep in mind that the people on the other end are brand new computer users and have XP.

So as it stands now, we use skype in linux so that I know when our relatives want to call us (but no video on linux), then we get them to wait a couple of minutes so we can reboot into windows to use Sightspeed.  A pain, I know, but for now the best solution.

---

### Post by patrick295767 on 2006-12-07
> **rsambuca said:**
> I hate to admit it, but as much as I like open source ubuntu, I can not find any solution to videoconferencing that even comes close to what is available in XP.  The only reason I still keep XP on my computer is for video conferencing.  We use Sightspeed so my daughter can talk and see her Grandparents across the ocean virtually every day.

While Sightspeed is a non-opensource solution, it works, and the video quality is much better than any other program we have tried.  I have tried many different linux to XP methods, but nothing comes close.  Keep in mind that the people on the other end are brand new computer users and have XP.

So as it stands now, we use skype in linux so that I know when our relatives want to call us (but no video on linux), then we get them to wait a couple of minutes so we can reboot into windows to use Sightspeed.  A pain, I know, but for now the best solution.

For sure, I would return to windows... The most unsecured operating system
 ...  I couldnt make it this jump back to prehistoric age.

Courage when u boot XP !! Be calm

---

### Post by kvonb on 2006-12-07
WENGOPHONE!

It has video, sound, and also incorporates ALL messengers: yahoo, msn, aim, icq!!

It is available in the add/remove progs from your main menu.  I installed it yesterday and it works perfectly, give it a try.

---

### Post by rsambuca on 2006-12-07
I find the quality is not even close to that of Sightspeed.  At least when I tried it.

---

### Post by kvonb on 2006-12-07
I have used skype for Windows in a vmware windows image, it works well for me.  Although you will need a pretty fast system for doing that.  The other benefit is that ALL webcams will work as you are running Windows, and also that you can stay in Linux :)

Regards, Kev :)

PS I just wish skype would get their arses into gear, that would solve all our problems!

EDIT:  I just read the terms and conditions of Lightspeed, it is the same as the other commercial apps in that it is an American company and all your information is collected and used for their own purposes.  Also (of course) the US government will have access to EVERYTHING.  I'd rather stick with the Europeans in that case, ie Skype or Wengo :)

---

### Post by burek on 2006-12-08
> **kvonb said:**
> I have used skype for Windows in a vmware windows image, it works well for me.  Although you will need a pretty fast system for doing that.  The other benefit is that ALL webcams will work as you are running Windows, and also that you can stay in Linux :)

Regards, Kev :)

PS I just wish skype would get their arses into gear, that would solve all our problems!

EDIT:  I just read the terms and conditions of Lightspeed, it is the same as the other commercial apps in that it is an American company and all your information is collected and used for their own purposes.  Also (of course) the US government will have access to EVERYTHING.  I'd rather stick with the Europeans in that case, ie Skype or Wengo :)

Pitty that the emulator WINE, it cannot be else because it is slow, could make work skype .... 

vmware would be too much for my machine

Thank you for your inforamtion !

---

### Post by kvonb on 2006-12-08
OK, I'm a blind idiot!

I just re-read the entire thread and the original poster stated quite clearly that Wengo was tried and was not what he/she wanted.

My apologies :rolleyes:

---

### Post by rsambuca on 2006-12-08
> I have used skype for Windows in a vmware windows image, it works well for me. Although you will need a pretty fast system for doing that. The other benefit is that ALL webcams will work as you are running Windows, and also that you can stay in Linux

So when running windows in vmware, do you use windows drivers for your hardware?  That would be convenient for me.

---

### Post by patrick295767 on 2006-12-08
> **rsambuca said:**
> So when running windows in vmware, do you use windows drivers for your hardware?  That would be convenient for me.

you have vmware tools to install
it s in it; in the menu bar of vmware

then you can use your usb; printer .... anythg you want
it s really like a normal windows pc

but but 
you need fast pc ! good CPU

---

### Post by arnieboy on 2006-12-08
I tested video and voice on wengophone 2.0 successfully last night.
Sound isnt as good as on skype (almost sounds like u got cookies in your mouth when u are speaking), video works fine.
wengophone 2.0 is very crash prone though (be prepared for frequent kills and restarts).
Other IM accounts work fine but when someone is "invisible" on yahoo and messages u, your reply box is disabled on wengophone (which is a major bug IMO).
A good way to avoid killing and restarting is not use wengophone as an alternative to gaim. Use wengophone only for video and audio calls to other wengo users and use gaim for the rest.
one more advantage is that file transfer works great (PC to PC) and you can send text messages to cell phones worldwide from wengo.

---

### Post by nalmeth on 2006-12-08
Arnie, were you communicating Ubuntu -> Windows? 

I've been trying to setup video conferencing for a while with my Dad, it's been hit and miss. 

We both have Wengo installed. When I call him, I can see his webcam, and my webcam, but he can't see either, and sound is extremely garbled for both of us. 

I've tried changing the codecs to no avail. On his side he has an audio config error, but this occurs on 2 different PCs, he thinks its Wengo at fault, and I have nothing to rebut. Firewalls all down, different sound cards selected (between video card/onboard).

Troubleshooting has been < enlightening. 

Qnext looks interesting.. Anyone please share experiences.

---

### Post by arnieboy on 2006-12-08
> **nalmeth said:**
> Arnie, were you communicating Ubuntu -> Windows? 

I've been trying to setup video conferencing for a while with my Dad, it's been hit and miss. 

We both have Wengo installed. When I call him, I can see his webcam, and my webcam, but he can't see either, and sound is extremely garbled for both of us. 

I've tried changing the codecs to no avail. On his side he has an audio config error, but this occurs on 2 different PCs, he thinks its Wengo at fault, and I have nothing to rebut. Firewalls all down, different sound cards selected (between video card/onboard).

Troubleshooting has been < enlightening. 

Qnext looks interesting.. Anyone please share experiences.
Nalmeth-
        Yes it was Ubuntu--> Windows and I was on Ubuntu. The audio config error might/might not be an issue. 
If its really an issue, you need the correct driver option loaded from the drop down menu under audio settings for audio input/output.
Even when you have got that right, you might see the audio error come up everytime you run wengo afresh. This can be resolved by changing any of the audio options to something else, hitting OK and then restoring it back to  
what it was and hitting OK again. Also, make sure you have muted "line in" from both alsamixer and gnome vol control if you are using your mic port on your pc. In any case, I could hear the voice of the person on the windows machine clearly, but my voice sounded a bit suppressed than on skype to that person.
as for firewall settings, I initially played around with the UDP ports but soon realized it was not affecting anything.

---

### Post by kvonb on 2006-12-08
Yes I had the problem with Wengo not echoing anything back to me with the audio test, I solved it by installing Firestarter on my server and forwarding port 5062 to my desktop then setting Wengophone to use SIP port 5062.  It had me swearing for an hour or so but worked well once I'd figured that one out :rolleyes:.  The sound is strange when I run Wengo on my server (Ubuntu Dapper 6.06) which is directly connected to the net, it sounds choppy, but on my desktop (Ubuntu Edgy 6.10) which connects to the net through the server, the sound is nearly perfect!  I can't tell if this is a version problem or a network problem though.  I also tried it with the official version which is in the Ubuntu add/remove progs section, and the beta version form their web site, both works perfectly for me.

Regards, Kev :)

---

### Post by RAV TUX on 2006-12-08
anybody try Ekiga Softphone?
[http://www.gnomemeeting.org/](http://www.gnomemeeting.org/)
[http://www.voip-info.org/wiki/view/Ekiga](http://www.voip-info.org/wiki/view/Ekiga)

---

### Post by arnieboy on 2006-12-08
a quick note on Qnext:
Its closed source and java based. It's feature packed and seems to be able to do whatever wengo can do and more.
I haven't been able to test voice/video yet.

---

### Post by arnieboy on 2006-12-08
> **RAV TUX said:**
> anybody try Ekiga Softphone?
[http://www.gnomemeeting.org/](http://www.gnomemeeting.org/)
[http://www.voip-info.org/wiki/view/Ekiga](http://www.voip-info.org/wiki/view/Ekiga)
have tried it several times in the last 5 years or so. It's like the Evolution of email clients (been around forever and is touted to be the standard but it will not improve much in the foreseeable future).

---

### Post by patrick295767 on 2006-12-24
> **RAV TUX said:**
> anybody try Ekiga Softphone?
[http://www.gnomemeeting.org/](http://www.gnomemeeting.org/)
[http://www.voip-info.org/wiki/view/Ekiga](http://www.voip-info.org/wiki/view/Ekiga)

I did it worked
sound was a bit choppy compared to skype

I still dont know how to make calls to normal fixe phone


Account Name: gizmo
Registrar: proxy01.sipphone.com
User: 1747645xxxx
Password: **********

Authentication Login: 1747645xxxx
Realm/Domain: proxy01.sipphone.com
Registration Timeout: 3600

---

### Post by wersdaluv on 2007-04-07
Bump. 

I hope people will post updated solutions here again.

I want to know the best means today of video calling from Ubuntu to Windows.

---

### Post by whirl on 2007-05-26
Im having the same problem. My gf is leaving to Germany soon and she wont istall ubuntu as I have no time to show her around ubuntu so we need prog which allows us to make video calls windows->ubuntu->windows.

I havent been able to try wengos videocall but it seems fine but there is one problem.. I tried that add a contact and added mr.Noone and now as I try to remove it crashes. This happens on my gf XP. Not a very good start..

Ekiga crashes immediately on this XP so its a no no.. Hope you guys find something for this one.

o/

---

### Post by wersdaluv on 2007-05-26
Until now, I am sticking with Gyache Improved for video and Skype for voice

---

### Post by mips on 2007-05-26
Can Skype be run in WINE ?  This is an option if you are at wits ends.

---

### Post by pirothezero on 2007-05-26
> **mips said:**
> Can Skype be run in WINE ?  This is an option if you are at wits ends.
It runs it but according to winehqs working catalog it does not support video as we speak.

I am liking the vmware/virtualbox idea I hadnt tried skype on there yet since I wont be needing video til this fall. I've installed the whole lot of them though but havent tested video yet with my mom or gf.

---

### Post by ramjet_1953 on 2007-05-28
Check out WengoPhone.

Basically the same as Skype, even calls to landlines. And unlike Skype it isn't crippled under Linux. Video calls and even encrypted calls.

[http://www.openwengo.org/](http://www.openwengo.org/)

Regards,
Roger :cool:

---

### Post by wersdaluv on 2007-05-28
> **ramjet_1953 said:**
> Check out WengoPhone.

Basically the same as Skype, even calls to landlines. And unlike Skype it isn't crippled under Linux. Video calls and even encrypted calls.

[http://www.openwengo.org/](http://www.openwengo.org/)

Regards,
Roger :cool:

Thanks, but it has been mentioned earlier in the thread

---

### Post by whirl on 2007-05-30
And wengo for some reason doesnt work at all on my ubuntu. I wish it would work for it seems like a good program :neutral:

---

### Post by jdavila27 on 2007-07-25
Here's my experience. For the last 6 month I've been traveling a lot and I needed to comunicate with my wife.

I have an HP Pavillion ze5300 laptop at home with Feisty. And I work with a laptop with XP so I needed something to comunicate between both XP and Ubuntu.

First we tried with text chat XP = MSN Messenger (Live) / Ubuntu = Pidgin (2.0.2)

- Excellent experience, no problems at all.

Next we tried with sound using Ekiga in both XP and Ubuntu:

- We had problems because the audio was awful, my wife at home could hear me, but I couldnt hear her, voice was very choppy.

So next we tried with Skype in both XP and Ubuntu:

- Super nice, great sound, we had some problems (probably because of the speed of my home connection) but then it worked perfectly.

So next step was video, and my first choice was Ekiga once again because I've already installed it on both computers:

- I bought 2 cheap webcams from Radio Shack (Gigaware). On XP the drivers installed perfectly and worked nicely on Ekiga.

- On Ubuntu it was a a bit difficult to make the webcam work. Thank God I found this site

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

the driver is called GSPCA, and supports my web cam Pixart PAC7311. You can find if your webcam is supported on the site.

Some instructions to install the driver can be found here:

[http://www.kaiser-linux.li/index.php/Linux_and_Webcams](http://www.kaiser-linux.li/index.php/Linux_and_Webcams)

- The other problem on Ubuntu with Ekiga was with audio, but I resolved it by upgrading Ekiga to version 2.0.9, the best way is to add the Ekiga repositories to Synaptic.

---------
Today we connected with Ekiga and sound and video worked fine!!!!

Well almost, I just have a problem with my audio in XP, it stops trasmitting a few minutes after connecting for no apparent reason. But then we still have skype so no problem.

We'll keep trying with Ekiga this week. 

Making stuff work in Ubuntu is so much fun, it's a great challenge sometimes but when you make it work it's just great. XP really bores me.

---

### Post by YannickDefais on 2007-07-25
Hi,

About Ekiga:
Please read the new documentation:
[https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)

If you experience really bad sound under Ubuntu, please upgrade to Ekiga version 2.0.9 as even Ubuntu 7.04 Feisty only ship 2.0.3 which is more than 1 year old. 2.0.9 comes with a lot of bug fix.

Ekiga isn't only compatible with Netmeeting, as Ekiga uses standards, it's **highly** compatible, see this list:
[http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F](http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F)

For those willing to use the windows version, a new version with improved support for webcams is out:
[http://ekiga.net/misc/ekiga-setup-2.0.10-BETA.exe](http://ekiga.net/misc/ekiga-setup-2.0.10-BETA.exe) (this is still beta, but should work better)

In the future, Ekiga will support much better video quality, especially with the use of the H.264 codec giving Ekiga the best quality available today with the lowest bitrate (but more CPU usage), see the roadmap:
[http://wiki.ekiga.org/index.php/Roadmap_to_3.00](http://wiki.ekiga.org/index.php/Roadmap_to_3.00)

Regards,
Yannick

---

### Post by Turtle.net on 2007-07-25
You should give wengophone a try.
Works great under ubuntu never tried with XP but should work ok ;)

I never tried the video (that&#347; why I'm interested in your experience)

Good luck :)

---

### Post by LookTJ on 2007-07-25
tried gizmo?

---

### Post by wersdaluv on 2007-07-27
> **Taylor said:**
> tried gizmo?

Does it support webcams?

---

### Post by loell on 2007-07-27
no , gizmo doesn't support webcam yet, but  to some, Video call can also mean voice and video,

you can use gizmo to call Yahoo and Msn messengers ,  and then youll just have to consolidate with other apps to do webcam, like amsn and gyachi.

---

### Post by rajeev1204 on 2007-07-27
wengophone doesnt work on 64 bit feisty  .Some bug confirmed .

Ekiga for me is distortion hell . And it seems to have trouble logging in too . And most of the time i just call the call test number . Who else do i call with these things ? Ubuntu users ? 

Wait for skype 1.5 !  Will have video .:)

---

### Post by YannickDefais on 2007-07-27
> **rajeev1204 said:**
> 
Ekiga for me is distortion hell . And it seems to have trouble logging in too . And most of the time i just call the call test number . Who else do i call with these things ? Ubuntu users ? 

Wait for skype 1.5 !  Will have video .:)

[Install last Ekiga 2.0.9]("https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c")
The Ekiga shipped by Ubuntu is at best 2.0.3, which is way old now.

[Ekiga is highly compatible, on any OS.]("http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F")

Who else do i call with Skype? Skype users only !

Regards,
Yannick

---

### Post by rajeev1204 on 2007-07-27
> **YannickDefais said:**
> [Install last Ekiga 2.0.9]("https://help.ubuntu.com/community/Ekiga#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c")
The Ekiga shipped by Ubuntu is at best 2.0.3, which is way old now.

[Ekiga is highly compatible, on any OS.]("http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F")

Who else do i call with Skype? Skype users only !

Regards,
Yannick

Heh ok thanks me will try new version . :)

And also what i meant was ekiga no one uses and also  SIP is unencrypted protocol unlike skype which i dont really care about but its the better way to talk iam sure .Safe and secure .

Ok thanks

bye now

regards

rajeev

---

### Post by YannickDefais on 2007-07-27
> **rajeev1204 said:**
> 
And also what i meant was ekiga no one uses and also  SIP is unencrypted protocol unlike skype which i dont really care about but its the better way to talk iam sure .Safe and secure .


Hi,

Sure there is less Ekiga users, than Skype users, but SIP users... I'm sure there is a lot of sip users worldwide.
e.g. read this : [Sip to become mainstream by 2010]("http://www.vnunet.com/vnunet/news/2193533/sip-become-mainstream-2010")
At least Ekiga.net telephony platform has more than 130 000 registrations as I speak now.

Ekiga can be encrypted (but I've never tried it) using [zphone]("http://zfoneproject.com/").
Ekiga will have built-in encryption for version 3.2

Some other SIP softphone already have built-in encryption like [twinkle]("http://www.twinklephone.com/").

Regards,
Yannick

---

### Post by jdavila27 on 2007-07-27
I've been using Ekiga this week (Ubuntu v2.09 <-> XP v2.09) and it's been working more or less fine with sound and video. I have trouble with sound in XP, haven't tried v2.10 (beta)

Yesterday I tried WengoPhone, and man, what a difference, video looks much better and audio is better too.

Ekiga works, but for me WengoPhone is just better in my case.

---

### Post by kotoro on 2010-12-20
> **styven said:**
> Thanks for hat , tried it no go.
I have tried other commands and get the following..............

Setting up build-essential (11.1) ...
styven@styven:~$ cd qnext
styven@styven:~/qnext$ ./congigure
bash: ./congigure: No such file or directory
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory
styven@styven:~/qnext$ make
make: *** No targets specified and no makefile found. Stop.
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory
styven@styven:~/qnext$ sudo make install
make: *** No rule to make target `install'. Stop.
styven@styven:~/qnext$ ./qnext
styven@styven:~/qnext$ ./configure
bash: ./configure: No such file or directory

Where am i going wrong?

Steve

Its java based right? So using build tools for C code isn't likely to get you anyplace.

Wow just noticed the 4 year gap, well hopefully my reply is useful to the next person that finds the thread. I"ll figure out how to properly launch it and put the answer here unless the mods lock it.

nope ./qnext worked fine, you need to use the dot slash and I suppose you could always chmod the qnext file to enable running it as a command. Its been several years, possibly the older version these posters were working with had problems.

---

### Post by madjr on 2010-12-20
the walking dead

---

### Post by samalex on 2010-12-20
> **madjr said:**
> the walking dead

No kidding... I started reading the original post about Skype for Linux not supporting Video and scratching my head... then I saw the date from 2006.

---

