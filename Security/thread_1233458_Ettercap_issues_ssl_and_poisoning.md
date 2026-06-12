---
title: "Ettercap issues ssl and poisoning"
date: 2009-08-06
forum: Security
---

### Post by thebigbradwolf on 2009-08-06
Alright, so I'm a big new to linux but gaining comfort with it. I've been playing around with ettercap and I absolutely love several of its features and the plugins are great as well, but I'm running into a couple of issues. The first being a simple lack of understanding. When I select my network interface before any sort of sniffing I get this line

 ```
SSL dissection needs a valid 'redir_command_on' script in the etter.conf file
Privileges dropped to UID 65534 GID 65534
```If someone could enlighten me I'm not sure if this is an issue or not. Aside from that I run chk_poison after selecting my targets and poisoning and get the following response:

```
Activating chk_poison plugin...
chk_poison: Checking poisoning status...
chk_poison: No poisoning between 192.168.0.133 -> 192.168.0.1
chk_poison: No poisoning between 192.168.0.130 -> 192.168.0.1
```Thank you in advance

---

### Post by fbnaia on 2009-08-06
Hi, saw your other post about ettercap, ettercap although a bit dated, it's still very usable, especially once you get started with filters and stuff.... First you have to make some changes in etter.conf.

Have a read here: [**http://openmaniak.com/ettercap.php**]("http://openmaniak.com/ettercap.php")


Also try this forum for more ettercap fun:

[**http://ettercap.sourceforge.net/forum/index.php**]("http://ettercap.sourceforge.net/forum/index.php")

It is a bit tricky to get it to work now on Ubuntu but it's doable..

Good luck.

---

### Post by thebigbradwolf on 2009-08-08
Thank you for the response. It's been a bit of a hairy process due to the issues with the gui crashing and the updated debs suggested by someone else on the forums. It's been difficult to concentrate on one issue at a time. But I'm just going to reinstall the regular ettercap packages from synaptic and start on the link you've given me and see how that works. Also, I was reading someone elses entry on a thread about ettercap crashes and it seems that the command line is going to be my best bet for a crash free instance of ettercap. Do you have any further advice to help clear up this murky subject for me? :-P I'm drowning in second hand advice the first hand stuff is much appreciated.

 Also, could anyone suggest a tutorial for setting up ettercap in ubuntu 9.04 including how to edit my etter.config? I have no trouble opening it, but what changes to make are a bit over my head. My last attempts to configure my etter.conf ended in the ettercap gui crashing up on my selecting unified sniffing (a problem that I thought I had fixed by installing some recompiled .debs suggested by [http://ubuntuforums.org/showthread.php?t=1160865](http://ubuntuforums.org/showthread.php?t=1160865)

HELP! ^_^

I forgot to mention that the ettercap forum doesn't see much traffic anymore and I found very little that help, but thank you for the reference.

---

### Post by fbnaia on 2009-08-09
Sorry, forgot to mention that i use the command line version of ettercap, but i know there are issues with the gtk interface. I am not on my Linux computer at the moment, but i remember i changed two things in etter.conf

edit the lines:

```
[privs]
ec_uid = 65534 # nobody is the default
ec_gid = 65534 # nobody is the default

to

[privs]
ec_uid = 0 # nobody is the default
ec_gid = 0 # nobody is the default

```
and near the end of etter.conf you see:

```
# if you use iptables:
#redir_command_on = "iptables -t nat -A PREROUTING -i %iface -p tcp --dport %port -j REDIRECT %rport"
#redir_command_off = "iptables -t nat -D PREROUTING -i %iface -p tcp --dport %port -j REDIRECT %rport"

to this

# if you use iptables:
redir_command_on = "iptables -t nat -A PREROUTING -i %iface -p tcp --dport %port -j REDIRECT %rport"
redir_command_off = "iptables -t nat -D PREROUTING -i %iface -p tcp --dport %port -j REDIRECT %rport"
```

Again this is from the top of my head, i will try to confirm this once i get home and edit if appropriate.

And for reference i am using ettercap command line version, installed from synaptic.

Good luck!...

---

### Post by thebigbradwolf on 2009-08-11
At the risk of sounding dumb or lazy; might you have any good resources for learning to use the command line version of ettercap? I've skimmed the man pages and a few other sources, but I run into errors which I believe are mostly in syntax. I've never run a program from terminal before so it'll be a new experience. Thank you very much for your patience so far..I do hope you enjoy schooling newbs :-).

---

### Post by fbnaia on 2009-08-12
Well, the main resources to learning ettercap (or any other program) would be to practice and have a lot of patience. In time you will learn the advantages of running programs from the command line, so eventually that will come easy if you keep practicing.

There are several good sites for beginners, one i often visit and recommend is [**www.irongeek.com**]("www.irongeek.com")

check this section on ettercap filters: [**Fun with ettercap filters**]("http://www.irongeek.com/i.php?page=security/ettercapfilter"), heres also a good "[**Tips and Tricks**]("http://forum.s-t-d.org/viewtopic.php?id=2594")" section from the [**s-t-d forums**]("http://forum.s-t-d.org/index.php").

I'm glad i can help you, keep practicing and good luck!.

---

### Post by TraceurJ on 2009-08-27
For some odd reasons I cannot save the edited etter.conf it Says "Write erro while ettempting to save (File name)" Why does it say that? Thank you

---

### Post by That_Guy_Smells on 2009-10-17
> **TraceurJ said:**
> For some odd reasons I cannot save the edited etter.conf it Says "Write erro while ettempting to save (File name)" Why does it say that? Thank you

Try opening it with the following command:
```
sudo gedit /etc/etter.conf
```
This should allow you to save it.

---

### Post by piyush.neo on 2010-08-03
hey!
while scanning the Host, my program crashes and i got this error
```

[piyush@localhost ~]$ sudo ettercap-gtk 

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA


(<unknown>:3208): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
Ooops ! This shouldn't happen...
Segmentation Fault...


```
Anybody have any idea...:(

---

### Post by cariboo on 2010-08-03
Please don't post your problem in more than one thread, I would suggest you request your two post be deleted, and start a new thread, instead of tacking your posts on to two old threads.

---

### Post by piyush.neo on 2010-08-03
Sorry! find the latter thread more intresting, so posted there too...

---

