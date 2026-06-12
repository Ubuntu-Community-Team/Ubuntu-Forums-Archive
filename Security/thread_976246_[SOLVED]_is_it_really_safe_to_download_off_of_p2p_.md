---
title: "[SOLVED] is it really safe to download off of p2p on ubuntu?"
date: 2008-11-09
forum: Security
---

### Post by shiningkenmonster on 2008-11-09
I heard on Windows when you download things off of p2p, it isn't safe.

i am not really sure.

when i go to command prompt on windows while i'm downloading something off of p2p and i type in 'netstat' or 'netstat -a'

it shows all the IP directly connected to me.

and its vice versa the other way around.

i heard from a hacker that he swap files and modifies. (on people who have windows)

is there a way to protect myself when i'n downloading off a p2p on ubuntu?

---

### Post by darkvampire on 2008-11-09
You are safe on Ubuntu as long as you don't give your P2P client sudo privileges or run it as root. :wink:

---

### Post by howefield on 2008-11-09
Depends on how you define "safe"

Safe as in virii or safe as in you won't get caught ?

---

### Post by darkvampire on 2008-11-09
> **howefield said:**
> Depends on how you define "safe"

Safe as in virii or safe as in you won't get caught ?


I didn't see it the other way.

For viruses; the chance of it happening is very very low; and you would have to be running it in sudo or root. To prevent this just get a virus scanner from the add/remove programs. Also, Avast! have made a anti-virus application for Linux (it is free as in price).

**Avast! Linux edition**
[http://www.avast.com/eng/avast-for-linux-workstation.html]("http://www.avast.com/eng/avast-for-linux-workstation.html")

For the don't get caught one; simply only use torrents to get software **legaly**.

---

### Post by shiningkenmonster on 2008-11-09
well, i'm talking about intruding your file systems and modifying them. since all people who are on a p2p downloads/uploads. everyone call see your IP directly.

is ubuntu just safer to use?

---

### Post by IshikawaNakano on 2008-11-09
Any time you have a program accepting incoming connections from the internet you increase the risk of your computer being compromised.

For example your p2p program could be vulnerable to a [remote exploit]("http://en.wikipedia.org/wiki/Exploit_(computer_security)") where somebody could run code as the user that you are running your p2p program which would also allow the to read your files. It could also be vulnerable to DOS exploits or exploits where somebody could read the contents of your file system.

Here are some examples (these are for windows programs but linux programs can and do have similar vulnerabilities):
[http://www.securiteam.com/exploits/5SP0L0AFHS.html](http://www.securiteam.com/exploits/5SP0L0AFHS.html)
[http://www.securiteam.com/exploits/5RP0R1P6AC.html](http://www.securiteam.com/exploits/5RP0R1P6AC.html)
[http://www.securiteam.com/exploits/5XP0D1F5FM.html](http://www.securiteam.com/exploits/5XP0D1F5FM.html)
[http://www.securiteam.com/exploits/5LP0M20F5M.html](http://www.securiteam.com/exploits/5LP0M20F5M.html)
[http://secunia.com/advisories/31441/](http://secunia.com/advisories/31441/)
[http://secunia.com/advisories/31445/](http://secunia.com/advisories/31445/)

If you do use a P2P program do not run it as root. Consider creating a new user with limited privileges to run the P2P program as.

---

### Post by lovinglinux on 2008-11-09
There are different types of p2p programs. The safest protocol is BitTorrent, because you don't share a folder, just files individually. So the peer on the other side cannot access your directory directly or see what other files you are sharing. So this drastically decreases the risk of someone tampering your files.

Additionally, BitTorrent applications check the file hash table and discard pieces that do not match the file you are downloading. So, there is no way to change the file content without your knowledge (as far as I know). Obviously that this doesn't help if you choose to download a tainted file, so you should download only form trusted and legal sites.

Nevertheless, virii is not an issue as already stated. So you are better protected using Ubuntu.

No matter what type of p2p application you are using, you have a service listening to incoming connections and connect directly to other peers (IP's). So, if the p2p application or the OS itself has vulnerabilities, then your system could be compromised. The good news is that vulnerabilities are discovered and patched much faster in Linux than in Windows.

No matter what OS or p2p application you are using, is a very good idea to use an IP blocking application. This kind of application will block connections from IP's "known" to be from hackers, spammers, virus distributors and other kinds of people with bad intentions. You don't have to know the IP's, because there are a few block list distributors (see [[COLOR="DarkRed"]**iBlocklist**[/COLOR]]("http://iblocklist.com/lists.php"), [[COLOR="DarkRed"]**TBG**[/COLOR]]("http://tbg.iblocklist.com/") and [[COLOR="DarkRed"]**Bluetack**[/COLOR]]("http://www.bluetack.co.uk/forums/")).

To block IP's on your Ubuntu machine you can use [[COLOR="DarkRed"]**moblock**[/COLOR]]("http://moblock-deb.sourceforge.net/") or [[COLOR="DarkRed"]**iplist**[/COLOR]]("http://iplist.sourceforge.net/"). I do recommend moblock, which is great and have excellent support [**here**]("http://ubuntuforums.org/showthread.php?t=803183"). Moblock is a command-line application, but can also download a frontend GUI called [[COLOR="DarkRed"]**mobloquer**[/COLOR]]("http://mobloquer.foutrelis.com/") (see moblock site for instructions).

Additionally, don't forget to use the built-in Ubuntu firewall (iptables) when sharing files. You can download simple firewall managers like Firestarter and ufw/gufw, that allow to easily create iptables rules.

If you are interested on BitTorrent applications, try Deluge. It is in the repositories, so you can download it with Ubuntu Add/Remove Applications. Deluge has all essential features, a nice interface and it is easy to configure.

Deluge also has a block list plugin, that can load lists from bluetack to block IP's, but it only protects your p2p application, while moblock and iplist protect your entire system.

You can learn more about p2p security [[COLOR="DarkRed"]**here**[/COLOR]]("http://forums.phoenixlabs.org/").

---

