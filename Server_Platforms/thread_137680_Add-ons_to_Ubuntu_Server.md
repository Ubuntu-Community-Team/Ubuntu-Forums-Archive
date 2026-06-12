---
title: "Add-ons to Ubuntu Server"
date: 2006-02-28
forum: Server Platforms
---

### Post by raghus on 2006-02-28
Minutes ago, I installed my first Ubuntu server on an old PC. Now I'd like to start downloading some software to it. My primary two applications are 1) a Firefox browser and then 2) XAMPP. I want to run this Ubuntu box as a LAMP server within my company.

Right now I have a unix prompt and not much else. Where do I go from here?

Thanks!

Raghu

---

### Post by dim_hyder on 2006-02-28
to use firefox you'll need to install a GUI

sudo apt-get install xubuntu-desktop

sudo apt-get install firefox

Dim_Hyder

---

### Post by dim_hyder on 2006-02-28
For LAMP

sudo apt-get install apache2
sudo apt-get install libapache2-mod-php5
sudo apt-get install mysql-server
sudo apt-get install php5-mysql

Dim_Hyder

---

### Post by raghus on 2006-02-28
dim_hyder: Thanks! Do I need to be in any particular directory before I can run the sudo commands?

---

### Post by Horndog on 2006-02-28
I hope you know that XAMPP Is not secure and is meant for Web Development only. As stated on there home page. There are ways to secure it to a point but it would not make a very good production server.

---

### Post by raghus on 2006-02-28
Whoops. I got an error:
"E: Couldn't find package xubuntu-desktop" 
I am logged in as root

---

### Post by raghus on 2006-02-28
XAMPP : yes, I know it is not bullet-proof but it's easy to get started with and I can move the configuration over to a solid PROD server at a later time

---

### Post by raghus on 2006-02-28
Also how does this sudo apt-get magic work? Do I need a CD in there or have these packages been installed and just need activation or is it connecting to the network somewhere? And once I run the apt-get for apache and php and mysql will it just "work" or do I need to tie them up with some configuration? (hence XAMPP...)

I'm quite new to installing Unix and additional software so any explanation will help.

Thanks

---

### Post by Horndog on 2006-02-28
[QUOTE=raghus]XAMPP : yes, I know it is not[color=red] bullet-proof[/color] but it's easy to get started with and I can move the configuration over to a solid PROD server at a later time[/QUOTE]

Listen:-# I said, it wasn't secure. I hope your job doesn't depend on this project.

---

### Post by raghus on 2006-02-28
Oh, well. Never mind XAMPP then. Can you help me w/the other qns?

---

### Post by zac1333 on 2006-02-28
Check this out, it should help you get Xubuntu on your old PC.

[https://wiki.ubuntu.com/InstallingXubuntu]("https://wiki.ubuntu.com/InstallingXubuntu")

---

