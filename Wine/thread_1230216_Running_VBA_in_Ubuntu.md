---
title: "Running VBA in Ubuntu"
date: 2009-08-03
forum: Wine
---

### Post by sau99ms on 2009-08-03
Hi,

I'm a newbie to Ubuntu (just switched a few weeks ago) and loving it - although getting my Netgear WG311v3 card working took some doing!!!

Anyway, not sure if this is the right place for this question but hoping someone will point me in the right direction here...is it possible to run VBA (Visual Basic) in Ubuntu or one of it's derivatives? I'm guessing as it's a windows application (?) that I'll need to run it in Wine?

Any thoughts/advice as I'm building an mATX system for a friend (duplicate of my new system - goodbye, beloved macbook!)

Thanks in advance!

Mark

---

### Post by Psicolonia on 2009-08-03
VBA is Visual Basic for Applicatiopns (runs inside Word, Excell, etc)

VB is Visual Basic is a native windows application. All of them usually run on wine. Make sure to install wine using:

apt-get install wine

you should also look for the VB runtime version 6 and install it before running any VB applications.

look here:
[http://appdb.winehq.org/appview.php?iVersionId=1325](http://appdb.winehq.org/appview.php?iVersionId=1325)

to see how to get VB6 Enterprise Running on Ubuntu, personally I would drop that, and go for gambas: [http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)

The language is basically the same although legally it cannot be a "copy" of VB6, however it's a good job for basic developers, very good and runs natively on linux so that you won't need to run everything with wine.

Also, take a look at RealBasic from RealSoftware if you are into VB and want to build native executables to Windows, Mac and Linux.

---

### Post by Mia1990 on 2009-08-06
vba runtime [winetricks]("http://wiki.winehq.org/winetricks") will install that for you.Hope this helps

---

### Post by sau99ms on 2010-03-15
Hi Psicolonia and Mia, thanks both for your replies - sorry it's taken so long to reply. I've been REALLY busy and forgot I posted that for a friend who's interested in ubuntu but too afraid to switch as she's afraid she can't do VBA on ubuntu.....

All the best,

Mark

---

### Post by asdfoo on 2010-03-15
to do 'VBA', you need microsoft office installed, depending on which version of office your friend has it may or may not work.

What they can do as an alternative, is run Ubuntu, but install Windows in Virtualbox (additional license for windows is required), and then run office inside VirtualBox.

VBA is heavily tied to MS office which is a complicated beast.

---

### Post by oldfred on 2010-03-16
Open office has its own scripting basic. I have converted one or two simple scripts from VBA to openoffice basic. They have to tools to assist but the syntax on some commands is a lot different.

---

### Post by sau99ms on 2010-03-16
Thanks to Asdfoo and Oldfred - I didn't know VBA was tied into MS although that open office option sounds promising. I'll try and look at that when I get chance. 

Cheers,

Mark

---

