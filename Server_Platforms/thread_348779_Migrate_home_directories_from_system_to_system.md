---
title: "Migrate home directories from system to system"
date: 2007-01-29
forum: Server Platforms
---

### Post by caveman56 on 2007-01-29
Hey all, got a quick query here that I'm hoping someone has had experience with.  I work at a small school and we're running a lab of Linux workstations, no windows at all, the kids love em.  What I would like to do is be able to setup the systems so that when a student logs in it copies their settings, backgrounds, etc from a central server.  I've seen LTSP and how to do diskless workstations, but I don't want to use the resources on the server to run everything as all these workstations do have hard drives, plenty or ram etc.  If anyone has any ideas, please let me know,

thanks,

Dave

---

### Post by kidders on 2007-01-29
Hi there and welcome,

To be honest, I would recommend against doing this, especially if you are concerned about placing too much load on your file server. Ignoring the fact that creating lots of copies of personal files causes endless complications in practical, day-to-day use, consider the I/O demand placed on a server when, say, ten people log in simultaneously, generating thousands of parallel requests for every file they own.

I'm very conscious this is ***not*** what you asked, but I wonder if you would consider sharing personal files over NFS. Bear with me for a sec...

**One potential issue**
This would have the advantage of spreading I/O operations to the server out over time, rather than cramming them all in at, for example, the beginning & end of class periods. You would eliminate head-wrecking complications that can occur when multiple copies of the same user profile exists and (a) a user logs into three computers simultaneously and makes irreconcilable changes to the same files, (b) network connectivity is lost momentarily or becomes unexpectedly slow, (c) you run into local filestorage problems.

**A second issue**
You suggested in your post that server load might be a problem. If you have enough computers to make the likelihood that someone will either be logging in or out at any given moment in time reasonably high, you can slash the amount of work a server has to do by avoiding associating these events with large copy operations. Now, consider that /home is really a symlink to /mnt/users, an NFS share that lives on a server. To reduce the load on a single fileshare even further, you could create 26 such NFS shares ... let's call them /mnt/users/users_a, /mnt/users/users_b, /mnt/users/users_c... You could then split them down the middle, and put each set on two different servers. Client-side, which one a user's files were really on would be irrelevant.

In addition, over the long term, you would have the infrastructure in place to introduce some redundancy into your network. Imagine that, even though /mnt/users/users_z and /mnt/users/users_a would be _shared_ by two different boxes, both boxes still contained up-to-date copies of both profile sets anyway. Now, one server blows a fan and melts down ... but your network stays up, because you still have a complete (albeit a bit slow) copy of all your users' data. Anyhow... that's off-topic... but might be worth keeping in mind.

Feel free to say "Answer my damn question, you idiot!", but I would feel bad if I did so without suggesting some worthwhile alternatives.

**Edit:** My post is premised on the assumption that you are catering for a reasonably large number of users ... say 50 to 5,000. I hope that wasn't foolish.

---

### Post by caveman56 on 2007-01-29
Hey thanks for the reply, definetly gives me some ideas to run with, we're running about 40 pcs on a school network, the major things is to give the students access in the classrooms to their profiles from the lab, same settings, etc.  LTSP works, but is a little too slow unless I can get it running with Xfce or IceWm.  Definetly thanks for the input.

---

### Post by kidders on 2007-01-29
> **caveman56 said:**
> LTSP works, but is a little too slow unless I can get it running with Xfce or IceWm.Yeah, LTSP probably wouldn't suit you ... and it would be a waste of your nice workstations, too!

If you'd like to give yourself an impression of an NFS-based solution, try this:

[LIST=1]
[*]Create a temporary share and mount it on a couple of test workstations.
[*]Do something like **head -c 1024m /dev/random > dummy** to create a gigantic dummy file.
[*]Try copying the file locally from both workstations at the same time.
[*]See how the server handles playing a movie while the copy is proceeding.
[/LIST]

With any luck, you'll be happy with network & server performance. If you felt like it, you could then mix in some RAID, which would dramatically improve I/O performance, and quota management, to keep your users on a leash. I've worked in a number of schools & universities that use a similar model, with good results.

---

### Post by jtc on 2007-01-29
> **kidders said:**
> 
[LIST=1]
[*]Do something like **head -c 1024m /dev/random > dummy** to create a gigantic dummy file.
[/LIST]

Myself I'd use **/dev/urandom** in this case.

The data won't be as random, but it will generate alot faster.

---

### Post by kidders on 2007-01-29
Good point! Thanks.

Since you're here, we might as well make use of you though! How would *you* go about centralising users' filestorage? Mounting a network share on top of /home with /etc/fstab _is_ the right thing to be recommending ... isn't it?

---

### Post by caveman56 on 2007-01-29
Thanks for all the replies, already started playing with nfs and think I have a working strategy.  My students are very good about logging out of their systems so we're going to work on setting all their directories on a central fileserver or two and have their home directories mounted to their from each machine.  One other question though, might not apply to this forum, any one know how to set the proxy settings in firefox for all users, hate to have to login to each account to set it up.

thanks again,

Dave

---

### Post by kidders on 2007-01-29
Firefox's user-specific preferences live at ~/.mozilla/firefox ... if you poke around in there, I'm sure you'll find where the proxy-related stuff is at. (I took a 2-minute look, but I didn't turn up what I was looking for.) A more straightforward alternative might be just to set up one generic profile (via the browser itself), tar it up, and unpack it into your users' homes. Preset the homepage, some useful links & the proxy information ... and you're sorted.

Package up the default Firefox profile with something like...
```
cd ~/.mozilla
tar -cf default_firefox.tar firefox
```

First time out, you could unpack it into every single user profile with something like this. It's quite a line, but at least it's just one step, and not 40!
```
for f in /home/*; do [ -x "$f/.mozilla/firefox" ] && echo rm -Rf $f/.mozilla/firefox; echo tar -C $f/.mozilla -xf default_firefox.tar && echo chown -R `basename $f` $f/.mozilla/firefox; done

```
For demonstration purposes I preceded each command with an "echo" to tell you what would happen, rather than actually *do* it, so you can double-check what I wrote doesn't have a daft mistake in it! Basically...

[LIST=1]
[*]Iterate over all files (directories) in /home.
[*]Test for the existence of .mozilla/firefox and remove it if necessary.
[*]Untar your pre-prepared "firefox" directory.
[*]If successful, extract the appropriate username from the directory path and chown the entire firefox profile accordingly.
[/LIST]

Of course, overwriting one individual user's profile is more trivial.

**Basic rule of thumb:** If you find yourself having to log into 40 accounts, you're missing something! In general terms, it's well worth accumulating little tarballs of useful default information like this, so that, when someone (invariably) does something silly, you can rescue them easily.

Something else that might be convenient (if you'll forgive me rambling on even further!) is /etc/skel ... the skeleton profile. When you look in it, be sure and add the **-a** flag to "ls", so you can *really* see what's there. I can't think of a reason not to put a default browser profile in there, so new accounts will be set up correctly whenever you **useradd** someone.

---

### Post by kidders on 2007-01-29
I know it's daft to be replying to myself, but something specific to your proxy question (rather than generally profile-related) just struck me. Have you considered transparent proxying?

The theory is that you would use your firewall (aka router) to intercept outgoing communications on, say, port 80 and redirect them to your www proxy. The primary advantage is that client-side proxy configuration would be completely unnecessary (ie your computers would simply think they had a direct connection to the web). The down-side is that, very occasionally, odd behaviour can sometimes result from a web browser's failure to accommodate a proxy it doesn't know it's using.

Provided your www proxy and internet gateway are the same machine, transparent proxying with squid is childsplay ... just in case you preferred that alternative. (Other network configurations make it slightly more involved.)

---

### Post by jtc on 2007-01-29
> **kidders said:**
> Since you're here, we might as well make use of you though! How would *you* go about centralising users' filestorage? Mounting a network share on top of /home with /etc/fstab _is_ the right thing to be recommending ... isn't it?

Yeah I'd say NFS is the way to go.

To simply  tell fstab to mount /home would no doubt work, but I think a better solution is to use the automounter. That way you only get the homedir belonging to the current user mounted.

What you should be aware of thought is that NFS is not really that secure. If you want to do this the Right way I'd suggestion you integrate NFS with Kerberos. To be honest thought, Kerberos is till on the todo list in the computerlabs I run.

---

### Post by kidders on 2007-01-29
One minor observation:

> **jtc said:**
> a better solution is to use the automounter. That way you only get the homedir belonging to the current user mounted.That would be sort of odd. On a standard Linux box, all users' files are usually mounted. Not having the option of allowing other users to drop things in your home directory, for instance, would be a bit awkward.

---

### Post by jtc on 2007-01-29
Very true.

Whatever you mount the entire /home or simply the current user's homedir both have their advantages. Which solution you want to use entirely depends on what kind of system you want and in which ways it is to be used.

---

### Post by thornomad on 2007-01-29
Doesn't Ubuntu have a "educational" version of the software that does, sort of, what you all have been talking about?  That is, run thin-clients off a centralized server (computers the kids use don't even have hard drives, I think) ?

I only read through this quickly, but am interested in the concept.

---

### Post by caveman56 on 2007-02-05
Yes it does, LTSP, which works, but unless you have some fast servers to run it from it slows down once you get more than 2 or 3 machines logged in.  Here we've got machines with hard drives so I'm looking to the NFS solution.  More than anything I want my students to have seemless access to all their files, desktop, etc on any machine they log into in the school, whether it be in the computer lab or in their classroom.

---

### Post by caveman56 on 2007-02-08
Hey JTC, sounds like we're kinda doing the same thing running labs, just wondering if by using NFS if there's a way to cluster multiple servers to handle the load.  I'd like to have maybe 4 servers around the school, but have the file systems always identical so it wouldn't matter which server they log into it would still have all the relevant data, but keep each server down to 5 to 10 people logged in to them at any given time.  Any ideas,

thanks,

Dave

---

### Post by jtc on 2007-02-08
Now I believe it is time for a disclaimer :) The answer I'll give now is not based on experience or solid knowledge, but is rather a qualified guess.

I have no idea how to cluster NFS-servers like that. I can easily foresee why it would be hard to get it working properly, but it is on the other hand quite possible that there is a clever wayI haven't thought about.

What I do wonder is why you want a solution like that, instead of one big NFS-server. Do you know there will be a problem with the load, or merely speculating? Will the load be on the network or on the nfs-server?

---

### Post by kidders on 2007-02-08
Hi again,

> **caveman56 said:**
> it wouldn't matter which server they log into it would still have all the relevant data, but keep each server down to 5 to 10 people logged in to them at any given time.That's an extremely small number! One properly configured file server should be well able to handle hundreds of simultaneous connections ... unless of course you have an extremely high-speed network, and your users are planning on battering the fileserver to death. (Basically, I'm wondering the same thing as jtc!)

All the same, what you're describing *is* possible ... but it's non-trivial. Most clustering solutions are designed to work in extremely high-volume HA environments storing massive amounts of data ... something you should expect to see reflected in the effort involved in setting one up. There *are* some more modest possibilities (such as GFS over AoE, for instance), but these tend to come with serious drawbacks in practical terms. That particular one would misbehave if you tried to use RAID to balance the vastly increased risk of hardware failure.

Out of interest, see what you think of the following:

Consider two servers (A & B), each with a pair of hard disks (A1 & A2, B1 & B2). A1 and B1 are exposed to the network using ATA over Ethernet. Server A composes a RAID 1 array out of disks A2 and B1, and Server B makes one with disks B2 and A1. The alphabet would be split between the two servers, [A - M] stored on server A's array, and [N - Z] on server B's one.

The result would be that, although the day-to-day load would be split between the two servers, each would contain a perfectly synchronous copy of all user profiles at all times, protecting you against the failure of one of them.

---

### Post by dalo on 2007-02-11
The solutions that you all may be looking for is allready there with the debian based
Skolelinux dist

It uses a central head server and lots of thin client-servers (ltsp) and all the /home dirs are placed on the head server.

[http://wiki.debian.org/DebianEdu/]("http://wiki.debian.org/DebianEdu/")

Skolelinux is the Debian-edu project's Custom Debian Distribution (CDD) in development. It is aiming to provide an out-of-the-box localised environment tailored for schools and universities. The out-of-the-box environment comes with 75 applications aimed at schools, as well as 15 network services pre-configured for a school environment. The simple, three-question installation requires minimal technical knowledge. Skolelinux is Debian, which means, among other things, that there are no license costs or worries, and that upgrade and maintenance of the software can be done over the Internet with the power of Debian's apt-get. The core goals of Skolelinux are localisation and ease of system administration.

---

### Post by pppetter on 2007-02-11
Dalo, he is not interested in LTSP. He is interested in having all home-dirs at a central server. Skolelinux and edubuntu have somewhat the same functionality, with LTSP and all of that, which has already been discussed. 

Please take some time and actually read what has been said in the thread the next time you post.

---

