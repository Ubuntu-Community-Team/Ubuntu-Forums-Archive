---
title: "Updating through Terminal as Firefox not seeing connection?"
date: 2006-08-04
forum: Repositories &amp; Backports
---

### Post by Carbonfish on 2006-08-04
Hi Everybody,

I have been scouring the forums trying to figure this out, and don't seem to be getting anywhere, so I thought that I'd try to come at it from a different direction.

I installed Dapper yesterday, and everything works (sort of) except I am having some trouble with my wireless configuration.  

I have a thread started in wireless support, but now it seems that the problem might be an apt-get thing. I am unable to load web pages even though I seem to be able to connect to an open wireless network. If I open Firefox it just spins it's wheels until it times out, but if I open the Terminal and type ftp ftp.debian.org, for instance, it says that I am connected to the server. Unfortunately, that server gives me an error (530 This is an anonymous server only) so that I can't do anything there (unless there is something else I need to know)

Until I get this resolved I can't update my system. And until I can update, I won't know if that resolves the network issue. 

I'm sort of stuck here.

I hope that I am not missing something obvious here and forcing you all to roll your eyes, but I'll be the first to admit, I'm a n00b.

TIA for you time and help.

Kent

---

### Post by bensexson on 2006-08-04
Try this command from the term window.  sudo apt-get update.  Does this work?

---

### Post by Carbonfish on 2006-08-04
Hi ben,

I tried that and it went through the apt-get process, but it just said that no packages were downloaded, installed, added, removed, etc. 

I am no longer in a place where I have a  reasonably fast network connection available (I am at home, and only have a dial-up connection here), so I can't try again to get you a copy of the terminal window info.

Oh yeah, I should probably mention that I am typing this on another machine, as I am still completely unable to access the interweb on the Dapper machine.

I guess that I will have to wait until tomorrow to continue this troubleshooting. It is sort of frustrating for me, and I'm sure for those who are trying to help me, because I only have a wireless network available at work (I work for the public school system), or through an "open network", like an internet cafe. And I can only drink about 22 gallons of coffee before I shake too much to type and have to go home.

This makes troubleshooting a PITA, but such is life I guess. :-({|= 

I really appreciate all the support, and I'll methodically follow all suggestions until this is resolved.

Thanks,

Kent

---

### Post by KaeseEs on 2006-08-04
If apt-get update runs through its list of 'gets' successfully, your connection is working.  Another quick test ( or three ) :


```
ping -c 5 google.com
```

If this gives you a packetloss figure < 100%, you are connected. 

```
apt-cache search firefox
```

If this returns a list of packages, you are connected.

```
 traceroute slashdot.org
```

If this returns a numbered list, you are connected.  If it returns an error like 'bash: traceroute: command not found', this just means you don't have traceroute installed; this provides yet another opportunity to test for a connection, by trying:

```
sudo aptitude install traceroute
```

Obviously, a succesful install indicates the presence of a connection, whereas quitting on a timeout indicates the lack thereof.

---

### Post by Carbonfish on 2006-08-04
Thanks to both of you, KaeseEs and bensexson,

I will get to a connectable (is that a word:?: ) spot first thing in the AM and try those helpful suggestions. 

I will update this thread as soon as I know more.

Thanks again,

Kent

---

### Post by Carbonfish on 2006-08-05
Good Morning everyone,

As per the last recommendations from KaeseEls, I tried to sudo apt-get update, but I got errors. 

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com 80 (1.0.0.0), connection timed out.

Then this error repeats for the archive, and then I get "failed to fetch" for the same reason

Then "reading package lists... Done
W. Some index files failed to download, they have been ignored, or old ones used instead.

Then I pinged google (ping -c google.com)
It seems to have gone through fine:
PING google.com (72.14.207.99): icmp_seq=1 ttl=245 time=85.4 ms
That goes on for 5 pings and then I get the summary that says that 5 packets were transmitted, 5 received, 0% packet loss, time 3998 ms

So I don't get it again. I seem to be connected, but I still can't load web pages.

Suggestions?

Oh yeah, I am in the same unenviable position of trying to do this at a coffee shop with an open wifi net. So I will stay and try to resolve this until they kick me out or I can't drink any more coffee.  :-P 

TIA for any help.

ps. Is there any way for me to copy and paste my terminal output to my iBook (the machine I am typing this on), and copy it into my posts so that you guys can see what's going on without my having to type it all in? I don't type as well as I did when I was younger, and it takes forever! :-({|= 

EDIT: One more thing, I just ran a traceroute, (traceroute slashdot.org) received bash: traceroute: command not found
So I did as recommended, (sudo aptitude install traceroute)
Output was:

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for traceroute
No packages will be installed, upgraded of removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


Thanks again,

Kent

---

### Post by KaeseEs on 2006-08-07
The probable reason that no candidate version of traceroute was found is that you don't have the 'universe' repository enabled ( if you need a quick explanation of repositories, look [ here]("https://help.ubuntu.com/community/Repositories"). )  To enable your 'universe' repository:

1)  Open your repository list as root:
```
gksudo gedit /etc/apt/sources.list
```
2)  Uncomment ( remove '#' from the front of ) any lines containing the word 'universe', especially any that look like:
```

deb-src http://archive.ubuntu.com/ubuntu dapper universe 

```
3)  Update your package lists:
```
sudo aptitude update
```
4)  Try and install traceroute again:
```
sudo aptitude install traceroute
```



    Now, back to the issue at hand, it would appear that your are able to connect to the internet in some fashion, but unable to access the web via firefox.  This is likely an issue of some sort with your internet gateway, but there's a chance that firefox is somehow out of whack.  You can try installing 'opera' ( another web browser ) via aptitude and check out if it works ( run the program from your terminal with no arguments ).  If your net is still on the fritz even through Opera... well, I hope someone smarter than I and more skilled in the ways of wifi responds to your bumped post.

NB - if you're wondering why sometimes 'sudo' is used and other times 'gksudo' is used for seemingly the same purpose, 'sudo' is used for command-line programs, while 'gksudo' is a version made to work with GUI/graphical programs.

---

