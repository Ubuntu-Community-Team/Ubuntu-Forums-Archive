---
title: "Best Ubuntu to Windows Yahoo"
date: 2011-12-11
forum: The Cafe
---

### Post by Georgescu1 on 2011-12-11
What is the best application if I am using Ubuntu and want to get the most features that a Windows Yahoo Messenger has?
I've tried:

-pidgin:video/audio doesn't work,pretty solid file transfer,the avatars refresh very rare

-kopete:video/audio doesn't work,the file sending function is not at all stable I was able to receive only 1 file out of over 20 tries and couldn't send any file (he got error),avatars refresh fast(as fast as on windows)

-Instantbird:doesn't have any video/audio or file transfer

I am looking for an application that I can enjoy a video and audio conversation with someone on yahoo,I didn't imagine some features that I considered "basic" on Windows are so rare on ubuntu.

---

### Post by 3rdalbum on 2011-12-12
> **Georgescu1 said:**
> What is the best application if I am using Ubuntu and want to get the most features that a Windows Yahoo Messenger has?
I've tried:

-pidgin:video/audio doesn't work,pretty solid file transfer,the avatars refresh very rare

-kopete:video/audio doesn't work,the file sending function is not at all stable I was able to receive only 1 file out of over 20 tries and couldn't send any file (he got error),avatars refresh fast(as fast as on windows)

-Instantbird:doesn't have any video/audio or file transfer

I am looking for an application that I can enjoy a video and audio conversation with someone on yahoo,I didn't imagine some features that I considered "basic" on Windows are so rare on ubuntu.

It's because the Yahoo (and MSN, AIM etc) instant messaging protocols are closed and must be reverse-engineered in order to implement these features on Ubuntu. The protocols change all the time, too; they must continually be reverse-engineered when they change.

Why not use something like Skype, where there is an official Linux client?

Or, if the person doesn't want to use a different messenger, use Meebo. It's like Pidgin, but it works through your web browser. Last time I checked, it could do voice and video - not natively through the IM protocol, but using a web-based helper called Tokbox.

---

### Post by LowSky on 2011-12-12
Google's solution works very well with Linux
[http://www.google.com/chat/video/index.html?hl=en](http://www.google.com/chat/video/index.html?hl=en)

I'm actually surprise many people still use Yahoo, AIM, or MSN these days. Their protocols are near ancient as the rest of their services are. Skype, Google Chat, and Facebook are really the big shots these days. My current AIM account is over 10 years old and my Yahoo account is probably 15. Barely does anyone ever contact me over those accounts.

Nowadays my friends just send text messages and emails mostly. IM was great before cell phones became super popular. Skype and Google are use the most if we need video conferencing.

---

### Post by Georgescu1 on 2011-12-12
> **3rdalbum said:**
> 
Why not use something like Skype, where there is an official Linux client?

Or, if the person doesn't want to use a different messenger, use Meebo. It's like Pidgin, but it works through your web browser. Last time I checked, it could do voice and video - not natively through the IM protocol, but using a web-based helper called Tokbox.

I can't tell all the people in my list "Hey install skype" cause they will answer with "hey install windows" which actually it's a better point of view because I am the only one needed to install something to have a normal conversation with them on the other side is making 60 people install skype just to have a videocall just with me.

And as for meebo..
***Note:****  If you're chatting with a buddy who is not  using Meebo Messenger they will be sent a link asking them to log in  through meebo.com.  The Video/Audio chat feature cannot connect directly  to an IM account not using Meebo Messenger.*




Facebook has that special feature that you can have a videocall on FB but then again is not very stable (most of the times don't even work) and ofcourse you have to install a plugin if i remember correctly and that's out of the question



so my adventure goes on :sad:

---

### Post by whiskeylover on 2011-12-12
I think yahoo has a web based messenger client.

---

### Post by Georgescu1 on 2011-12-13
It doesn't have audio/video call.

The thing is I don't get it , what the people that make the apps for linux think.I mean there are over 20 apps for multi IM and they are basically the same thing,the same features,only different gui.It reminds me of the old times when I was playing in visual basic,making a photo editor and sharing the code on youtube.The next week 5 apps with the same functions as mine were "developed".

They should unite and make 2 apps with incredible functions than 20 with sad ones.

---

### Post by DangerOnTheRanger on 2011-12-13
> **Georgescu1 said:**
> It doesn't have audio/video call.

The thing is I don't get it , what the people that make the apps for linux think.I mean there are over 20 apps for multi IM and they are basically the same thing,the same features,only different gui.It reminds me of the old times when I was playing in visual basic,making a photo editor and sharing the code on youtube.The next week 5 apps with the same functions as mine were "developed".

They should unite and make 2 apps with incredible functions than 20 with sad ones.

Ah, the old "why don't FOSS developers unite" question. There are quite a few reasons why this isn't the case:
[LIST]
[*]NIH syndrome (quite common)
[*]The developers of the applications in question disagree on fundemental parts on how such an application would be implemented
[*]The 20 (for argument's sake) applications differ at the philisophical level, making it impossible to combine them
[/LIST]

Like 3rdalbum said, it's not like Yahoo has documented their IM protocol - these developers are having to reverse-engineer that protocol by themselves without any help from Yahoo, which is not an easy task. Plus, when Yahoo changes their IM protocol (without any warning, of course), what do you think happens? ;)

What you should do is check Pidgin and Kopete's respective websites to see if anyone else wants Yahoo video chat, and lobby for that feature to be implemented in Pidgin and/or Kopete. If you really want Yahoo video chat, you could pay one of the Pidgin or Kopete developers to implement it, if you wanted.

---

### Post by stalkingwolf on 2011-12-13
for general yahoo messenger with cam I use Gyache, it also has as i recall
voice capability.

For voice chat i use google chat more often than skype.

---

### Post by cgroza on 2011-12-13
> **stalkingwolf said:**
> for general yahoo messenger with cam I use Gyache, it also has as i recall
voice capability.

For voice chat i use google chat more often than skype.
Isn't that client dead?

---

### Post by TenPlus1 on 2011-12-13
Open the terminal and run the following commands:

 sudo add-apt-repository ppa:adilson/experimental
 sudo apt-get update
 sudo apt-get install gyachi

This will let you install Gyachi on Ubuntu 10.04 to 11.10...  enjoy!

---

