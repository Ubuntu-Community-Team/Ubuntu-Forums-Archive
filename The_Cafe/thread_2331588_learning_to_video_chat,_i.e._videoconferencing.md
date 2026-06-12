---
title: "learning to video chat, i.e. videoconferencing"
date: 2016-07-23
forum: The Cafe
---

### Post by haplorrhine on 2016-07-23
This might go in Multimedia or The Cafe because I'm requesting advice and requesting that somebody video chat with me.

I need to test out video chat with somebody since my family is all tied up.  It is more complicated than expected, partly because my hard drive failed and my persistence flashdrive isn't persisting.  I don't have a Facebook account to use Facebook Chat, but 12.04 Live has Empathy by default, and on 16.04 Live [Google Talk installs]("http://ubuntuhandbook.org/index.php/2014/05/install-google-talk-plugin-in-ubuntu-14-04/") quickly and easily.  I made an AOL AIM account for Empathy, but I'm reluctant to share it.  However, for Google Hangouts, I made a google account specifically for this: [EMAIL="haplorrhine@gmail.com"]haplorrhine@gmail.com[/EMAIL]
I am wondering about compatibility between clients.  Apparently Facebook dropped the open-source XMPP protocol, forcing Empathy users to install unsupported packages that conform to the Facebook standard, but does that require a Facebook account anyway or could I talk to a Facebook user through an AIM account logged in via Empathy?  That is, do I need to login a different type of account depending on which client my chat buddy is using?

Thank you and warm regards.  I can only add tags from 16.04, not on 12.04.5

---

### Post by gordintoronto on 2016-07-23
I think the world's most popular videoconferencing software is QQ, which does not work in Linux for video. Next would be Skype. [sigh] Its "options" will check your hardware very well. I am rarely online, as gordintoronto, but "YiRui Su" is often online.

Replacing a failed hard drive doesn't require much money -- and you might be amazed with the performance of a small (60GB or more) SSD. Eg:
[http://www.newegg.ca/Product/Product.aspx?Item=9SIA7RD2WU4966](http://www.newegg.ca/Product/Product.aspx?Item=9SIA7RD2WU4966)

---

### Post by jonjon2 on 2016-07-25
I think in general when it comes to things like Skype and Google Talk, yes you have to make sure the other person on the other end of the conference call is using the same platform. There is a lot of software out there though for business and project management that includes conference calling. I'm not exactly sure what platform it uses and if the other person needs to have the same thing, you would have to look into it. I think Bitrix has conference calling, and iMeet is specifically designed for conference calling. You could check those out. I haven't used the conference calling function in Bitrix, just the project management and group chat functions. I also haven't used iMeet, so....you're guess is as good as mine. I'm sure there must be an option out there that allows you the option to connect via Google Talk or Skype or whatever....you know, that lists all of the biggest platforms so that you can contact your meeting partners in what ever form they use, while you don't need to switch between platforms. And IF this doesn't already exist, then someone really needs to get on building this. That would be a program that would absolutely sell.

---

### Post by haplorrhine on 2016-07-30
Thank you for the suggestions.  Now I'm not sure I will need it immediately, but I'll definitely have it figured out in the next few months or so.

---

### Post by haplorrhine on 2016-08-12
[s]I will probably be on for the next 5 hours and through the days after this.[/s]  It's easy enough to install Empathy on 16.04. see below.

sudo add-apt-repository "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe"
sudo apt-get update (I would like to be specific rather than update the entire system, but it works.)

It will be a few more days actually.  Furthermore, I'm not sure the  necessary ports are open on the public wifi, and I can't seem to use  nmap to test the server ports.  They probably disabled port scanning for  security purposes.  I don't see why they should disable the ports for video chatting as long as they can limit bandwidth, but alas I don't know.

[s]I will be on during the next few hours.[/s]
I can only use my standard Google account for Empathy on 16.04, which requires installing it to RAM first.  Subsequently running it eventually causes a system freeze.  Unfortunately my hard drive is broken.

---

