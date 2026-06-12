---
title: "GUI log analysis (not web based) - what exists?"
date: 2011-06-12
forum: Server Platforms
---

### Post by Oceanwatcher on 2011-06-12
I am looking for a desktop application that can read logs from a Ubuntu Server and let me sort/search/analyse them in different ways to see what is going on.

This is primarily for the normal logs in the system, not web statistics. But I also welcome suggestions for desktop apps for webstats as well.

Yes - I know about several web based ones, but that is not what this thread is about :-)

I have been searching the net and this forum, but it is extremely difficult to come up with a search string that give anything useful.

---

### Post by cariboo on 2011-06-13
Have you look at the log file viewer that installed on the default Ubuntu desktop?

---

### Post by Oceanwatcher on 2011-06-13
First - I am using Kubuntu on my desktop. But Ubuntu Server on the server.

Can you use the normal log viewer to connect to logs on a remote server? How do you do it? Over SSH?

I could not find any obvious ways of using the normal log viewer in Kubuntu to do this. It would at least need a profile setting so that you can switch between local and remote logs...

---

### Post by arrrghhh on 2011-06-13
> **Oceanwatcher said:**
> First - I am using Kubuntu on my desktop. But Ubuntu Server on the server.

Can you use the normal log viewer to connect to logs on a remote server? How do you do it? Over SSH?

I could not find any obvious ways of using the normal log viewer in Kubuntu to do this. It would at least need a profile setting so that you can switch between local and remote logs...

You could just forward X over ssh, but this might put more tax on the server than you want to put up with - that's what I do if there's something on the server that must use a GUI.

---

### Post by Oceanwatcher on 2011-06-13
Ehrrm... No X on this Ubuntu Server :-) No GUI on the server. What I would like to do is download the logs to my laptop and analyze them there.

There must be someone that has made a program that can be used for digging through logs without being on the computer where the logs has been made?

---

### Post by arrrghhh on 2011-06-14
> **Oceanwatcher said:**
> Ehrrm... No X on this Ubuntu Server :-) No GUI on the server. What I would like to do is download the logs to my laptop and analyze them there.

There must be someone that has made a program that can be used for digging through logs without being on the computer where the logs has been made?

It's forwarding the traffic over the network to another machine... so X isn't exactly running on the server per-se...

But if you don't want to install anything related to that on the server, I understand.  Hopefully others have a better solution for you, as I'm not aware of one.

---

### Post by rothbert on 2011-06-20
Looking for exactly the same thing...

---

### Post by arrrghhh on 2011-06-20
> **rothbert said:**
> Looking for exactly the same thing...

What's wrong with forwarding the X session over SSH?  It honestly seems like the best option to me, as there doesn't seem to be any off-the-shelf solutions for this problem.

---

### Post by volkswagner on 2011-06-20
I don't see the benefit or need for GUI application for log files.  Please this is not a dig, and I'm truly curious what functions I may be missing.  

From the server or ssh session use less.

I like to use less, especially in ssh session for easy highlighting/copy of text.  It has a simple search function and easy navigation.  You can even run it against compressed/archived files with no added switches.

```
less /var/log/syslog
```

You can pageup/pagedown or arrowup/arrowdown for one line at a time.  Search for a string: search starts with /

Enter a date and/ time to jump to location.
```
/Jun 20 08:27:34
```


Enter a keyword:
```
/init
```

then you can use 'n' to jump to next instance or <shift>+n for previous.


So I respectfully ask, what is gained when using a GUI?

---

### Post by rothbert on 2011-06-20
Thanks arrrghhh and volkswagner - 

So I occasionally want to cross check a stats program with actual server log files - and was having to do so today and realised how much easier it would be to have the data in front of me in a more manageable form - ie formatted into columns according to date, IP, page visits etc.

Also realised this wouldn't be a difficult thing to do, wondered if anyone had had the same thought.

Haven't used less or tried an X session over SSH as its not something I do regularly but will look at those.

cheers

---

