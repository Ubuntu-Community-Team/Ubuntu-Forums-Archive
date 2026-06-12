---
title: "Ad-Aware"
date: 2008-02-29
forum: Security Discussions
---

### Post by Gloominati on 2008-02-29
Hello. I'm looking for similar software to Ad-Aware 2007 i have good experiences with this one, is there anything similar or you do not really need anti spy ware for linux?

---

### Post by jrusso2 on 2008-02-29
If you want to run something like adaware on Linux there is nothing like that mostly because there is no spyware on Linux.

If you want something like that for windows try spybot search and destroy

---

### Post by Gloominati on 2008-02-29
So i should be afraid of overloaded HD with spy wares??

---

### Post by aysiu on 2008-02-29
Do not change networking defaults unless you know what you're doing, use strong passwords, do not use untrusted software repositories, and do not log in as root, and you should be fine.

---

### Post by seanc7 on 2008-03-02
Currently, there's very little worry about spyware on Linux or any Unix-derived system. Virtually all spyware is written to target Windows.

I haven't heard of any spyware for Linux.

Now to help protect Firefox or any of it's derivatives, you can install an addon called NoScript - basically it blocks all scripts, flash, javascript, etc. If you want a script to run you have to explicitly allow it.

---

### Post by OrangeCrate on 2008-03-02
> 
**Browser / Spyware : Java/Flash/Ad-ware/Trackers/Cookies**

This is where most users will have the most risk. We all want Java/Flash, but our Internet browser opens us to attacks.

I advise :

   1. Deny all cookies and add trusted sites, allowing only for session.
   2. Install NoScript. Again block all and add trusted sites to a white list.
   3. Install Safe History
   4. Adblocking : I block with a hosts file rather then Adblock Plus or Adblock Filterset.G because a hosts file protects more then just firefox.
          * [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)
          * Linux script : [http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)


[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Ad-Aware, and Spybot are Windows programs.

Though frankly, I've never heard of spyware on Linux, I do use NoScript, and Adblock Plus with the three EasyList add-ons. See here:

[https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

[http://easylist.adblockplus.org/](http://easylist.adblockplus.org/)

Filterset G is not suggested to be used with Adblock Plus:

> **Do I need to install Filterset.G Updater?**

No. Actually, it is recommended not to use Filterset.G with Adblock Plus. There are several reasons for this:

    * Filterset.G has been intentionally made incompatible with the built-in subscriptions feature in Adblock Plus, updating Filterset.G requires a separate extension which basically duplicates existing functionality.
    * Filterset.G is not optimized for use with Adblock Plus, it will slow down your browsing considerably more than any other filter list.
    * Filterset.G makes heavy use of very complicated regular expressions with the consequence that finding the source of problems is difficult and fixing those problems is even more so. In fact, Filterset.G is fixing most problems with exception rules which creates a problem on its own (see next point).
    * Filterset.G contains a considerable number of exception rules. This is a big problem because exception rules cannot be overridden. It happened on several occasions that exception rules from Filterset.G whitelisted actual ads making these ads unblockable — something users usually blamed Adblock Plus for.

While Filterset.G has had its uses in the past, nowadays other filter lists are certainly a better choice. If you already have Filterset.G Updater installed, you can uninstall the extension and remove the Filterset.G subscription in the Adblock Plus Preferences dialog. Feel free to choose any subscription from the list then.


[http://adblockplus.org/en/faq_project#filterset.g](http://adblockplus.org/en/faq_project#filterset.g)

---

