---
title: "Replace Windows XP Server with Ubuntu"
date: 2009-02-24
forum: Server Platforms
---

### Post by mitanc on 2009-02-24
Hey all, I am on a business trip and my office calls me to tell me our windows server is crapping out, internet's not working, and I am losing money on all the downtime.  Immediatly Linux has popped into my mind.

Some background, I know linux, I know ubuntu.  I run a desktop ubuntu version at home, I got fileserver, video sharing, music streaming all the good stuff.  

Anyways, I basically need some guidance on what I can and cannot do.  This is a list of what needs to be able to be done:
1.  File Serving 
  a.  I have about 10 clients using shared folders, they all need to have proper access to everything.  All clients are windows XP machines, I want to know if I can set permissions for each machine?

2.  Remote access to file shares
  a.  Does anyone know where I can begin reading about this.  Say I am in a hotel with my laptop, I would like to be able to access my shared folders from there.

3.  File searching
  a.  I would love it people could get on a website hosted by my machine and search for files (pdf, word, excel, etc.) not only filenames but content as well.  Worst case is I install a desktop search client on the windows client machines and ask them to index the shares.  

4.  File sync w/ FTP
  a.  I need to sync some files on my server with an ftp site as a backup / lookup for other offices to see.  Is this possible?

Other than that I think all my other needs are covered with linux.  Does anyone else have a linux server running at work and know any tips or ticks?

Appriciate all's help with this.  Thanks!

Mitan

---

### Post by HermanAB on 2009-02-24
Yes, you can do all of that is various ways: Samba, OpenVPN and proftpd come to mind.  However, if you don't have time to tinker with setting it up manually, then you should consider using a more mature version of Linux, eg Suse or Mandriva, since they have wizards for everything.  You can have it all running in an hour using Mandriva using only a few mouse clicks, while it will take a while with Ubuntu if you are not familiar with Linux already.

Cheers,

Herman

---

### Post by mitanc on 2009-02-24
Thanks for the tips.. I like ubuntu because of the repository.  File sharing via samba is easy with webmin I think and VPN I can use logmein hamachi, which I heard is great!

Does mandrake use repositories?  I just love the apt-get install, by far the most innovative thing I have ever used or seen.

Mitan

---

### Post by HermanAB on 2009-02-24
All the various Linux distributions are the same deep down.  Ubuntu use the Debian package management system and Mandriva use the Redhat method - both systems work at the click of a mouse.  Mandriva and Suse have wizards for *everything*, while Ubuntu has wizards for most things.  

Which ever system you use is a personal choice, but sometimes in the interest of expediency, it is better to use a system with lots of wizards.  If you have ever used Windows 2003 or 2008 server and thought the wizards are pretty good - well, Mandriva and Suse are better than that.  Give Ubuntu another 3 years and it will be the same.

Cheers,

Herman

---

### Post by 3L33T on 2009-02-24
> **mitanc said:**
> 
1.  File Serving 
  a.  I have about 10 clients using shared folders, they all need to have proper access to everything.  All clients are windows XP machines, I want to know if I can set permissions for each machine?


Use SAMBA for file sharing.  Lots of examples and documents on google that will enable you to do what you want to do.

> 
2.  Remote access to file shares
  a.  Does anyone know where I can begin reading about this.  Say I am in a hotel with my laptop, I would like to be able to access my shared folders from there.



I use apache webserver to do this when I need to serve my files for public access (with password protection).  I simply create a symbolic link (ln -s shared_folder_dir_path link_name) of the shared folder in my web root folder.  That way, all files in the shared folders are also viewable to public via http.  Run a dynamic dns service (like dyndns or tzo) if you do not have a static ip address from ISP.

> 
3.  File searching
  a.  I would love it people could get on a website hosted by my machine and search for files (pdf, word, excel, etc.) not only filenames but content as well.  Worst case is I install a desktop search client on the windows client machines and ask them to index the shares.  


THAT IS EASY, create a php or shell script with a dialogue box that runs 'find' or 'locate'.  

> 
4.  File sync w/ FTP
  a.  I need to sync some files on my server with an ftp site as a backup / lookup for other offices to see.  Is this possible?


I'm running something similar to this:  I basically created a shell script that creates a tar archive of files I want to synchronize (ftp over) to another server.  I used 'cron' to schedule that job to run nightly and ftp's it over to another server.  Works like a charm! ;)

> 
Other than that I think all my other needs are covered with linux.  


Right, why would you need to use the O.T.H.E.R operating system when linux is highly customizable?


HTH

---

### Post by freerkkalsbeek on 2009-02-24
Consider FreeNX for remote access to your system. 
Another approach would be SSL-VPN which only needs an HTTPS connection, so even a PC in an internetcafe can give you secure access to your documents.

In the past I've used SSL-Explorer for that, but they changed their license. The GPL version is now available as Adito ([http://sourceforge.net/projects/adito/](http://sourceforge.net/projects/adito/))

Good luck,
Freerk

---

### Post by mitanc on 2009-02-26
Thanks for the tips and suggestions guys!  The one thing I love about Linux is once its running I can basically SSH in and tinker with it to get just about anything working.  This means even though I have a business to run, I have the ability to come home at night and setup things which I normally would wait for an IT professional to do or just not do at all.  This brings on maximum efficiency! 

I think I have all the tools I need to get corporate IT functionality at a fraction of the cost and bringing my business to the next level.  

After everything I read it seems I can do much more than I have been doing, the only drawback which I have always had with linux has been the enabling of print server with my linux box.  I currently have a color laser epon printer (I don't know the model number off hand) but if I can get that to work I am basically set.  

I am also thinking about setting up RAID for my new server, any tips on hardware that anyone has experience with.  I am running a company in China, and I am not Chinese.  This means there's a huge communication problem and the main thing I don't want to happen is get hardware which doesn't work off the bat.  

Thanks for your help again!

---

