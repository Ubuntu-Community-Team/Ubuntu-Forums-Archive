---
title: "sites-enabled .... :evil:"
date: 2006-02-01
forum: Server Platforms
---

### Post by dbee on 2006-02-01
Can someone pls tell me exactly what to do with sites-enabled / sites-available.
I've read the docs but I can't seem to get it right. 

If there is one thing that really pisses me off about linux ... it's the fact that every hacker somewhere reckons he's come up with a new and different way of doing something which was very easy to do in the first place. If it ain't broke then don't fix it I'd say.

IMO cutting httpd.conf into four or five different files doesn't make it easier to manage. Site-enabled/available is a mess, why do I need a tool to enable my sites ?

If there is some debian hacker somewhere who is under the impression that this makes apache easier to administer. Then pls let me be the one to inform you otherwise. Oh, this is so frustrating, not to talk about a waste of my time. I have to go back and work on my p3 windows laptop AGAIN.... :-#

Help ...

---

### Post by LordHunter317 on 2006-02-01
[QUOTE=dbee]it's the fact that every hacker somewhere reckons he's come up with a new and different way of doing something which was very easy to do in the first place. If it ain't broke then don't fix it I'd say.[/quote]Monolithic configuration files are never easy, unless they're exceptionally small.

> IMO cutting httpd.conf into four or five different files doesn't make it easier to manage.Multiply that by 100 and then you understand.

As for an actual problem do you have one?

---

### Post by dbee on 2006-02-01
[quote]
Multiply that by 100 and then you understand.
[quote]
... well ok, but then how many people use ubuntu as a 'monolithic' server. 

I'm not just trying to sound off on ubuntu here. I think it's a great distro, and I'm very appreciative of the hard work and effort that the developers and others put into it. 

I'm on ubuntu64, which I know is an unsupported version. I like linux and I really don't mind all the various sound issues, nvidia driver issues, writing your own firewalls, having different programs which all use various versions of glibc, the flash issues, the java issues and so on and so forth ... there is nothing that ubuntu can do about any of these issues for the time being at least,

so I count the time I put into getting my system to just work everyweek, as time well spent. It's just that when it comes down to something as basic as apache. I really have a problem with the fact that someone has gone out of their way to make things more difficult than they are already. If I ran 200 websites then I might appreciate the extra thought that ubuntu puts into apache. But I don't, I just want to be able to work at what I do - using ubuntu as my OS. 

If apache want to change how their program runs then fine. Or if I want to install a program which runs apache differently then that's ok as well. But if every distro does things a different way by default, then I'm going to be wasting an awful lot of time on something that really isn't going to benefit me in the long-run. 

I'm far from an expert when it comes to apache, but I do write my own config scripts (usually) and I try to do my own compilations as well (even though I know that it's not recommended). So it's kind of aggravating when I have to relearn the wheel on ubuntu, just because someone somewhere decided that scattering httpd.conf, putting in various other mods/sites - enabled/available folders,  various links from one file to another, adding extra tools and altering the directory structure is now the 'easiest way to do things'. The documentation doesn't really give much away either for that matter.

LordHunter: I know that you are now going to WOW me with some unbelieveable expert linux knowledge regarding various issues which I won't understand. But honestly from my point of view it seems like ubuntu/debian should stick  to doing what they do best - which is making great distro's. And leave other people's programs up to them.

---

### Post by MJN on 2006-02-01
Have you checked out the thread from post #10 at [http://www.ubuntuforums.org/showthread.php?t=117866]("http://www.ubuntuforums.org/showthread.php?t=117866") ? It should get you on the right road and we can fill in any gaps as they arise..
 
Mathew

---

### Post by LordHunter317 on 2006-02-01
[QUOTE=dbee]If I ran 200 websites then I might appreciate the extra thought that ubuntu puts into apache. But I don't, I just want to be able to work at what I do - using ubuntu as my OS. [/quote]Well, it's not like the changes aren't documented or are an issue.

And if anything, the setup is *easier* for people new to apache, not harder.  Why?  They apt-get install whatever DSOs they need, and then edit a single, small file that's relevant to exactly what they care about.


> But if every distro does things a different way by default, then I'm going to be wasting an awful lot of time on something that really isn't going to benefit me in the long-run. Without getting into standardization arguments, realize there would effectively be only one distro if they were all exactly the same.

> So it's kind of aggravating when I have to relearn the wheel on ubuntu,There's no wheel to relearn.  If you cant' grasp seperate files in a minute or so the frankly, you won't ever understand how to properly deploy apache.

>  The documentation doesn't really give much away either for that matter.Yes, it does.

>  But honestly from my point of view it seems like ubuntu/debian should stick  to doing what they do best - which is making great distro's. And leave other people's programs up to them.It wouldn't be great if they didn't make these sorts of changes.

---

### Post by olddog55 on 2006-02-01
dbee:-

I agree with you re: the hacking of configuration files.  I too find that having a multiplicity of configlets is annoying and much prefer the monolithic approach.  To me, one file seems so much easier to read/understand.

I've read the other posts in this thread, and while I think I can understand some of the rationale, I don't agree with it.

I've also found that I can usually force the config file back into the monolithic format. :-)  [ Apache and Exim ]  Just keep a backup copy available for when they do a distribution upgrade, as they seem to take delight in forcing the config back into configlets.  :shock:

---

### Post by diebels on 2006-02-01
One good reason for splitting conffiles is functional automatic updates. If you edit /etc/apache2/apache2.conf , dpkg won't update it, or if it did, you would loose your configuration. It's better to have extra files sourced.

Read /usr/share/doc/$packagename/README.Debian to get some hints when you're confused

In apache2-common's case, you are directed to /etc/apache2/README which gives a very clear explanation of the conffile layout

---

### Post by darth_vector on 2006-02-02
[QUOTE=dbee]Can someone pls tell me exactly what to do with sites-enabled / sites-available. I've read the docs but I can't seem to get it right. [/QUOTE]

you should have one file in site-available for each website you are hosting (if you dont have a domain and are going by IP address you will only have one site).

in sites-enabled create symlinks to the sites in sites-available that you want to publish.

thats all there is to it.

---

