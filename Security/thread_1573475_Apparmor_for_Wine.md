---
title: "Apparmor for Wine"
date: 2010-09-12
forum: Security
---

### Post by malfa89 on 2010-09-12
Hello,

I have been an on and off user of ubuntu and I need some assistance related to apparmor. I really like ubuntu but I really dislike the openoffice suite. So I installed wine to run Micro$oft Office and I want to protect my files from being infected and accessed through wine. I read bodhi.zazen's post and scoured the forums looking for an easier explanation but I am just not that advanced of a user. While using apparmor I did the following on the terminal.

sudo /etc/init.d/apparmor start

Then,

sudo genprof/home/****/.wine

It ran the whole process and asked for a username over and over. So I attempted to generate a profile again. Eventually I was tinkering around with it and used:

sudo /etc/init.d/apparmor start

Subsequently, I lost all my office related files and my office related programs. Could someone please assist me in an easy to use tutorial to confine wine using apparmor. Thank you so much.

Don A

---

### Post by bodhi.zazen on 2010-09-12
First you need to decide what you wish to restrict and what you with to allow.

You then restrict a binary, wine, now ~/.wine

I suppose you could confine ~/.wine/c_drive/Program\ Files/name_of_exe , but you probably want to restrict the wine binary.

genprof will generate a very generic file, you restrict or allow access via

full_path permissions,

for example

/home/your_user/.wine/** rwix,

You may want to start with a simpler application and look at some sample profiles.

---

