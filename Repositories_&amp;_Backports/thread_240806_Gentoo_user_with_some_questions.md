---
title: "Gentoo user with some questions:"
date: 2006-08-21
forum: Repositories &amp; Backports
---

### Post by thewierdone2000 on 2006-08-21
Hey,

I had two questions for anyone willing to listen.

My first question, as stated in the title, is how often does Ubuntu update its packages? I currently use Gentoo, but wouldn't mind switching to Ubuntu Edgy, assuming the software is (kept) up to date. 

Currently Edgy features almost all the latest in terms of the software I want, but how often is this updated? For example, Dapper Drake doesn't feature nearly as up to date packages as say Gentoo.

My second question is for anyone who has used Gentoo before, and that is, is there any Ubuntu equivalent to eix. For those of you who don't know what eix is, it is a very fast way to locate packages available, and show the various versions available to download. I am aware apt-cache show does this kind of, but not nearly as well. Is there such a tool (that runs in a CLI) for Ubuntu?

Lastly, to anyone who used Gentoo before, any words of wisdom on whether or not to switch? Do you miss anything in Gentoo? Are you welcomed by things in Ubuntu?


Thanks.

---

### Post by snaga on 2006-08-21
I used Gentoo for a couple of years, and then switched to Ubuntu about 18 months or so ago.

I really liked Gentoo, and still have nothing bad to say about it. Its a great distro, IMO.

I decided to switch to Ubuntu because I didn't want to compile anymore. I finally decided that any benefits that I received were outweighed by the need to compile.

I have found Ubuntu to be great. I think the forums are as good as the Gentoo forums, which I liked alot.

When there is an Ubuntu release, the versions that are in that release are locked. From that point on, that release only gets security related updates. I'm sure there is a point in time when Edgy will no longer get new versions of software, so it will begin to get behind. For many programs, there is the possibility to get a backport for your Ubuntu release.

For me personally, Gentoo was getting updated with new versions a little too often. It was causing me a some grief.

Ubuntu is great. I don't consider myself a 'flavor of the week' distro person. I rarely change distros. Ubuntu is the 5th I've used since I started using Linux in '95. I was with Gentoo a long time, and I plan on being with Ubuntu even longer.

---

### Post by thewierdone2000 on 2006-08-21
Thanks for the response. A few questions, if I may.

You said "backports" of software would be availible, what are those exactly? I am sure I could always get the source, but then it becomes a hastle because apt doesn't know some programs are installed, even if they are (unless I am missing on some of the features of apt? like telling it something from source is installed? or converting source to a .deb perhaps?)

Also, did you ever use eix? Is there something like it for apt?

---

### Post by UbuWu on 2006-08-21
You can use checkinstall to make apt aware of the programs you install from source. Basically it goes like this:

./configure
make
sudo checkinstall

One of the best things about this is that you can easily remove the program if you want to using apt.

---

### Post by UbuWu on 2006-08-21
Backports: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by thewierdone2000 on 2006-08-21
Thanks UbuWu

---

### Post by BadSquishy on 2007-05-18
I found this thread while trying to answer a specific question.  The question is, for my Dapper Server will the Ubuntu devs ever update Samba from 3.0.22 to a new version (currently feisty uses 3.0.24)?  

It would be great if someone could confirm that the answer to my question is this: as long as I keep the dapper-backports repository disabled I will continue to receive security updates for Samba 3.0.22 but will never receive an update to a newer version of Samba.  

I needed to find out about this because I am also a Gentoo user and I simply did not know how package updates are handled in Ubuntu (or any other distro for that matter), I only knew that Gentoo handles it different than most.  Also, I have used a third party .rpm to enable on-access virus scanning in Samba and the .rpm was compiled specifically for 3.0.22, so if I was updated to 3.0.24 it would most likely break on me.  

Well, theweirdone2000 is probably not paying attention to this thread any longer, but hey, I've never even heard of eix, I'm gonna try it out as soon as I get home to my Gentoo boxes.  

I've decided to use Ubuntu Server 6.06 LTS for a file server I have set up at work.  I've gone with Ubuntu over Gentoo for two reasons.  First, if things go awry for some reason I can't figure out, I can call up Canonical with a company credit card number and get some help.  Secondly, the setup and maintenance of a Gentoo machine is more time and CPU intensive, and is just not necessary in this situation.  The benefit does not make up for the increased work.  But I think Gentoo is a great operating system, especially for desktop machines and "power users".  I'm wearing my "I'd rather be compiling." T-shirt right now, as a matter of fact.  

Well, enough rambling.  If someone in-the-know reads this, please take a minute to answer my question.  

Regards

---

