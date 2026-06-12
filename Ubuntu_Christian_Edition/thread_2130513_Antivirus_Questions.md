---
title: "Antivirus Questions"
date: 2013-03-29
forum: Ubuntu Christian Edition
---

### Post by parkernathan on 2013-03-29
Hope everyone's having a blessed Good Friday!

A couple quick questions about antivirus. Do I really even need to worry about antivirus on Ubuntu CE? 

If I do, what's the best solution to install/run and antivirus app? Command line or GUI? I've installed clamav through the command line before on Linux servers I've worked with.

Also, do I need to do any configuring to the firewall or just use it out of the box?

Thanks a bunch!

---

### Post by PhantomTurtle on 2013-03-29
You can read this thread for more about security on Ubuntu, [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) (scroll down to the firewall section and the viruses section).

In my opinion, Ubuntu is generally safe to use without the need for much configuration if you are careful.

Additionally, Ubuntu CE comes with Dansguardian, which uses clamAV to scan and block viruses from file downloads. So you should be fairly safe with file downloads.

If you want to be extra careful, install clamAV.

For firewall, Ubuntu comes with ufw(uncomplicated firewall) installed by default. If you want to manage it using a gui, install Gufw (sudo apt-get install gufw).

You can also use Firestarter as a firewall if you want to. Instructions on how to install that is one here - [http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/).

Hope that helps :)

-Phantom

---

### Post by stlsaint on 2013-03-29
The only way your system will be compromised is if you allow it ;)

Opening up ports without monitoring them, giving exe's free reign to run on your systems by providing them your root password, etc.

---

### Post by parkernathan on 2013-03-29
Thanks both for the info! 

@PhantomTurtle Good general article on security. Was great to look over and sharpen my skills. Nice to know DansGuardian uses clamAV already for checking downloads. Very nice plus. Thanks for the firewall tips as well.

@stlsaint Thanks for the pointers as well. I may run all my Windows apps under Windows in a VM instead of WINE, plus running other Linux servers and Macs, I'm familiar with firewall and root password cautions, so great pointers to remember. I think my computing environment on the Ubuntu CE side will be pretty much secure.

Plus I'll be removing Java and limiting what Flash can do, so I'll even have a few less vulnerabilities. :-)

BTW, for those needing to run a Windows VM on their machines, as well as those on Android phones, I've found a good Christian-based security software firm called. Thirtyseven4. I'm looking at switching to them for my security needs for Windows and Android. They donate part of their profits to ministries, so it's a nice plus knowing I'm helping ministries with my software purchases.

---

### Post by Stonecold1995 on 2013-03-29
> **parkernathan said:**
> A couple quick questions about antivirus. Do I really even need to worry about antivirus on Ubuntu CE? 
I think the question is, do you need to worry about antivirus on *Ubuntu*.  Ubuntu CE and Ubuntu are essentially the same when it comes to security, so anything that applies to Ubuntu is very likely to apply to the CE version as well.

Just read through some of the similar questions on the non-Christian section, and I'll bet it'll apply completely to CE.

---

### Post by parkernathan on 2013-03-30
> **Stonecold1995 said:**
> I think the question is, do you need to worry about antivirus on *Ubuntu*.  Ubuntu CE and Ubuntu are essentially the same when it comes to security, so anything that applies to Ubuntu is very likely to apply to the CE version as well.

Just read through some of the similar questions on the non-Christian section, and I'll bet it'll apply completely to CE.

Yep, true. :-) I do understand that Ubuntu CE and Ubuntu are identical in base code that both are based off of Ubuntu, but it sure is great to have an edition of Ubuntu geared toward Christians/ministries. The team has done an amazing job with Ubuntu CE, and I hope they keep up the great work!

---

### Post by lisati on 2013-03-30
> **Stonecold1995 said:**
> I think the question is, do you need to worry about antivirus on *Ubuntu*.  Ubuntu CE and Ubuntu are essentially the same when it comes to security, so anything that applies to Ubuntu is very likely to apply to the CE version as well.

Just read through some of the similar questions on the non-Christian section, and I'll bet it'll apply completely to CE.

Good answer. There is no shame in seeking wisdom about available tools and techniques.

It might seem a little overwhelming at first, and sometimes there are seemingly contradictory opinions, but there is a wealth of information to be found in the[ Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") section of this forum.

---

### Post by parkernathan on 2013-03-31
> **lisati said:**
> Good answer. There is no shame in seeking wisdom about available tools and techniques.

It might seem a little overwhelming at first, and sometimes there are seemingly contradictory opinions, but there is a wealth of information to be found in the[ Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") section of this forum.

Thanks for the link on that as well. I might have a look.

Hope everyone is having a great Easter!

---

