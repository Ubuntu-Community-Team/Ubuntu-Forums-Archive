---
title: "Two servers with nothing to do"
date: 2009-11-09
forum: The Cafe
---

### Post by hambone79 on 2009-11-09
I need a little help in deciding what to do with a couple of servers that I have, but first I need to give a little background on what I do and what I'm currently using my other computers for...

I do contract mechanical engineering work out of my house and collaborate on projects with two other engineers by allowing them to tunnel into my network. Most of the services I need to run are consolidated on a single RAID-5 server that is running eBox. It handles my file shares, acts as my domain controller, runs a printer server, and handles all of my backups. For most of my day-to-day work, I have one computer running Linux and one computer running Windows. 

Since most of my daily work is handled by those machines, I now have two servers that are sitting around doing nothing. One is an old 1GHz P3 machine with 80GB of storage, and the other is an Athlon XP machine with about 4GB of RAM, and 750GB of storage.

I'm thinking about setting up a FTP server on the P3 machine so that customers can upload files to me, but I'm not sure what to do with that Athlon machine (maybe a virtual machine server of some type?).

Anybody have any suggestions?

---

### Post by kpholmes on 2009-11-09
check out my signature

---

### Post by The Real Dave on 2009-11-09
Give back to the community and use rTorrent to seed some Ubuntu torrents if you have the bandwidth :lolflag:

Or you could donate them to me......


Or maybe something like Folding@Home?

---

### Post by BackwardsDown on 2009-11-09
Run a freenet/tor to support the anti-censorship movement:p

---

### Post by Bachstelze on 2009-11-09
Run NTP and join the NTP pool.

[http://www.pool.ntp.org](http://www.pool.ntp.org)

---

### Post by RiceMonster on 2009-11-09
Set up ssh and give out the login on a public web forum.

---

### Post by dragos240 on 2009-11-09
> **RiceMonster said:**
> Set up ssh and give out the login on a public web forum.

>.<

I have become infamous.

---

### Post by jmore9 on 2009-11-09
Post well and meaningful daily messages !!

---

### Post by The Real Dave on 2009-11-09
> **dragos240 said:**
> >.<

I have become infamous.

You didn't O.O ](*,) </shocked>

---

### Post by dragos240 on 2009-11-09
> **The Real Dave said:**
> You didn't O.O ](*,) </shocked>

I set up an SSH server, I gave out a username and password to the server. The user had no rights. They could only make files. Of course. They could also crash the server with a few scripts, such as fork bombs. Stupid avahi! I shut it down. The server died of something else. Ah well!

---

### Post by The Real Dave on 2009-11-10
> **dragos240 said:**
> I set up an SSH server, I gave out a username and password to the server. The user had no rights. They could only make files. Of course. They could also crash the server with a few scripts, such as fork bombs. Stupid avahi! I shut it down. The server died of something else. Ah well!

Well, thats one way of testing how much cr*p your server will deal with :)

---

### Post by hambone79 on 2009-11-11
Ok, I think I have it figured out now...

1. I am going to use the P3 machine as an FTP server.

2. I am going to use the Athlon machine to run Torrentflux and BOINC.

I figure giving my spare CPU cycles and bandwidth to the community is the best option :)

---

### Post by beercz on 2009-11-11
I was going to suggest using the spare server as a backup server using [rnsapshot]("http://rsnapshot.org").

---

### Post by ZankerH on 2009-11-11
> **dragos240 said:**
> I set up an SSH server, I gave out a username and password to the server. The user had no rights. They could only make files. Of course. They could also crash the server with a few scripts, such as fork bombs. Stupid avahi! I shut it down. The server died of something else. Ah well!

I had a similar experience with giving out SSH accounts to random people.

-Someone runs a forkbomb, tells me how to protect from it
-I restrict users to 200 processes.
-Someone dd's zeroes on my /var, which I stupidly put on the same partition as /. 
-I somehow salvage the server, put /var on a seperate partition
-Someone runs a script that takes up all the ram and swap space. Kindly enough, he teaches me how to restrict ram and disk usage afterwords.
-The system should be pretty locked down about now, right?
-Some guy still managed to find a basic privilege escalation exploit, promptly runs rm -rf /


I mean, I did this fully expecting to get the server raped, but I was still a bit surprised. Lesson learned, you don't give /g/ free stuff and get away with it.

---

### Post by hambone79 on 2009-11-13
> **beercz said:**
> I was going to suggest using the spare server as a backup server using [rnsapshot]("http://rsnapshot.org").

I thought about that, but I have a set of external hard drives that I use for backups. That way I can rotate them regularly and keep one copy off site in a safe.

---

### Post by Sporkman on 2009-11-13
Maybe you could run some sort of number crunching jobs on it.

Or you could have it serve up a website, perhaps some sort of technical forum or perhaps a portfolio of your work.

Or, you could just set it up as a clone of your current server, in case your current one crashes or dies, then you could do a quick switchover.

---

### Post by pookiebear on 2009-11-13
I say turn them off and save on your power bill. Or use them as dead servers. Only turn them on to copy stuff to them.

---

### Post by hambone79 on 2009-11-15
> **Sporkman said:**
> Maybe you could run some sort of number crunching jobs on it.

Or you could have it serve up a website, perhaps some sort of technical forum or perhaps a portfolio of your work.

Or, you could just set it up as a clone of your current server, in case your current one crashes or dies, then you could do a quick switchover.

Way ahead of you there...all of the computers on my network are running as part of the World Community Grid ([http://www.worldcommunitygrid.org](http://www.worldcommunitygrid.org)).

As far as the website goes, I have a technical blog/forum at hacksawlabs.com and my portfolio is at hygear-design.com.

---

