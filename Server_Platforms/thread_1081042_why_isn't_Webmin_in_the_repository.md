---
title: "why isn't Webmin in the repository?"
date: 2009-02-26
forum: Server Platforms
---

### Post by memilanuk on 2009-02-26
Hello,

Picked up a spare PC today to setup a small home server on.  It's been a few years since I got out of the Linux scene, but one of the programs I remember from back then is Webmin.  So now I see all sorts of posts about installing webmin on Ubuntu... but it's not in the repository.  I think I saw somewhere that the Debian webmin deb file would probably work just fine; I realize that downloading and setting up a default webmin install isn't exactly rocket science.  I'm just curious what exactly the beef is with webmin; I got the impression that (some of) the ubuntu developers didn't like it much at all (think I read a comment along the lines of 'had a party when we finally yanked it from the repository' or something to that effect).  Any idea what thats about?  I presume they have good and solid reasons for feeling that way... does webmin just not play nicely with the default config files on ubuntu?  I seem to recall that being an issue way back when (talking 5+ years ago) when I first used it - going from distro to distro it was always a challenge to figure where a particular config file had moved to and how the default format had changed, etc. so I could see how that might be an issue for developers.

TIA,

Monte

---

### Post by memilanuk on 2009-02-26
Sure 'nough... after searching and reading and then finally postnig a question... I came across the answer (at least part of it) while looking for something else.

[https://help.ubuntu.com/community/WebMin]("https://help.ubuntu.com/community/WebMin")

Open mouth, insert foot, chew vigorously ;)

I guess the question still remains... so many people appear to be using it successfully on ubuntu... so why not a *ubuntu* package of webmin, even if it's not in the Debian package system.  Or is ebox just the offically sanctioned and annointed choice and thats that?

---

### Post by bab1 on 2009-02-26
> **memilanuk said:**
> 
...Open mouth, insert foot, chew vigorously ;)

I guess the question still remains... so many people appear to be using it successfully on ubuntu... so why not a *ubuntu* package of webmin, even if it's not in the Debian package system.  Or is ebox just the offically sanctioned and annointed choice and thats that?

The first paragraph says it all. > dropped because it is not compatible with the way that Ubuntu packages handle configuration files, and caused unexpected issues with people's systems.

What more needs to be said?

---

### Post by memilanuk on 2009-02-26
Guess I just find that seems odd with the number of glowing recommendations and tutorials on Webmin + Ubuntu that even a casual search pulls up.  Granted, there are some 'what happened?!?' threads too, but not so many as to make it seem like some horribly insurmountable problem.

I thought this sounded more like the key issue:

> 
It should be blindingly obvious that these packages are not really being
maintained anymore.  I have always been more or less the only person looking
after them.  I have had a lot of positive feedback from users (and even some
money on occasion) but I'm finding less and less time and motivation to keep
at it.  It is better to drop them now rather than perpetrate the cruel joke 
that these are Debian-quality packages; especially because newbies often 
rely on webmin to administer their systems and keep them secure.  And we owe
it to Jamie Cameron, the author of webmin, not to besmirch his name and product 
with buggy crap.

...which being circa 2005 and over on Debian, not Ubuntu... was why I was asking about it *here*.

---

### Post by bab1 on 2009-02-26
Once again:> ...now rather than perpetrate the cruel joke
that these are Debian-quality packages...

Sounds the same to me.  You are aware that Ubuntu is Debian based?

The idea is to NOT modify the distro when the package configures itself.  

Unsupported just makes it worse:
> It should be blindingly obvious that these packages are not really being maintained anymore.

---

### Post by Brazen on 2009-02-26
> **bab1 said:**
> Once again:

Sounds the same to me.  You are aware that Ubuntu is Debian based.

The idea is to NOT modify the distro when the package configures itself.  

Unsupported just makes it worse:

Webmin has it's own apt repo, so you could just use that.  I've pretty well moved away from Webmin to doing everything command line and in the long run, I think I like that better.  But I do still use Webmin for firewall administration, and when you are learning it's nice to be able to have a nice gui to "get the job done" while you figure out other parts of the system.

---

### Post by memilanuk on 2009-02-26
> **bab1 said:**
> You are aware that Ubuntu is Debian based?

I was aware that it was Debian-based; I didn't understand that to mean that if Debian drops a package because one of their package maintainers doesn't feel like keeping up with it that it cannot be considered by Ubuntu.  Ubuntu does have its own package maintainers, no?  What happened three years ago in Debian due to lack of interest there shouldn't condemn a package now in Ubuntu, should it?

> The idea is to NOT modify the distro when the package configures itself.  


Well, that is kind of what I'm getting at - I saw references that the Ubuntu developers don't like it, but no real explanation of why.  I see the Debian list messages and bug reports that it had first been orphaned, then later removed from the tree.  I see references that it does bad things to config files... which as I mentioned above, I can easily understand given the disparate ways in which various distros go about their core config files.  

Where that stops making sense is I see a lot of people *using* Webmin on Ubuntu, and one would presume Debian, successfully.  If it was that broken, I'd expect to see more complaints at the user level.  Then we have an actual webmin .deb file (as mentioned above, thank you) so that would lead me to think that the webmin developers are aware and working with Debian/Ubuntu systems at some level, or they wouldn't be so brave as to put a .deb file up on *their* site.

Could someone perhaps explain *specifically*, with examples, where webmin goes astray from the Debian/Ubuntu config file philosophy - using small words and keeping in mind that I haven't been working with this stuff for a number of years ;)  

I don't necessarily have a problem with using the CLI to set up or maintain a machine... but for some things I think it's a bit simpler/easier to be able to 'see' things in a GUI.

Thanks,

Monte

---

### Post by Rich_B_uk on 2009-08-07
Was thinking exactly the same as the OP.

Webmin is running at 1.480 (Released 11th June)
Debian package at **their** site is upto date.

Fair enough, back in 2005 it was obviously a broken as regards Debian, but there appear to have been few problems since then from what I can see. I think the OP was simply looking for someone in authority or with extensive experience to give them an update.

I for one am happy to use it. Yes, terminal is better in the long run, but we all need to learn - and we're not all that experienced with doing everything from the terminal.

Just my 2p!

---

### Post by samosamo on 2009-08-07
Life wouldn't be the same without it for me.  I manage ~10 ubuntu servers with it. Virtualmin too.

---

### Post by Rich_B_uk on 2009-08-07
I'll certainly give that a shot as well if I'm ever in the position of having to do extensive web server configuration.

It's either that or getting lost for weeks until one finds their feet in Apache config :P

---

### Post by castrojo on 2009-08-07
> **memilanuk said:**
> I was aware that it was Debian-based; I didn't understand that to mean that if Debian drops a package because one of their package maintainers doesn't feel like keeping up with it that it cannot be considered by Ubuntu.  Ubuntu does have its own package maintainers, no?  What happened three years ago in Debian due to lack of interest there shouldn't condemn a package now in Ubuntu, should it?

Yes but likely if a package is in poor shape in Debian that doesn't mean there's necessarily someone interested in working on it in Ubuntu. 

I find ebox to be much better anyway. Think of it as natural selection, heh.

---

### Post by memilanuk on 2009-11-10
Sorry I missed out on the last few responses... at any rate, I am glad to see that some other people think its worth a try.  I'm in the process of getting things settled down here, then I'll probably give it a whirl on my machine here.  It's been off-line most of the time since my original post due to just not having time to mess with it :(

---

### Post by hgerstung on 2009-11-24
(sorry for the long post)

My project: Last week I set up a new (headless) homeserver for myself, using an Atom N230 board, an eSATA 32GB stick for the system partition and adding my existing 3 SATA HDDs to the mix afterwards. My software needs are Samba, DHCP+DNS and Cups. 

I started setting up 9.10 server on a USB stick for a first test, adding webmin and was able to get everything up and running after ~2 hours. I was extremely satisfied with that, given the fact that I barely know anything about DHCP and DNS configuration and only the basics when it comes the Samba. Doing this in 2hrs would not have been possible without webmin for me, simply because I am not managing Ubuntu servers on a daily basis and I would expect to spend at least 2 hours on learning how to put together my (admittedly simple) configuration. For example: How to set up bind and dhcpd to enable automatic resolving of hostnames for dhcp clients? Easy if you know how to do it, I know. You just have to find the howto for this on Google and follow it. But using webmin was just faster than this. 

When I received my eSATA stick afterwards, I decided to start from scratch before I would replace my (8.04 running existing homeserver) with the new box. Installing Karmic server on the new stick, adding webmin manually and recreating the initial configuration from scratch took me only ~1 hour. 

I accept that there are plenty of environments where you are lost without a SSH login and a commandline, but I believe there are tons of people who want a simple, graphical administration interface for their headless homeserver and a lot of them are not familiar with putting together a (working) configuration for bind, dhcp, samba, cups and so on.

Since webmin is claiming to support Ubuntu (and does that pretty good IMHO), I would say that there are no technical reasons why this should not be included in the repo. If there are issues with the way how webmin handles configuration files or problems that cause configuration hiccups, I am pretty sure that there is a way to fix it. I did not experience any problems besides the fact that the DHCP module defined a key after using it in the same config file, which triggered an error in the DHCP server config. I just used the "Edit config file manually" button, moved the key definition above the section where the key is used and pressed the "save" button. Afterwards, it worked like a charm. 

My oppinion: Please, add it to the repo! Do not use a three year old argument, because both Ubuntu and Webmin have been developed and are in much better shape today. 

Regards,
  Heiko

---

