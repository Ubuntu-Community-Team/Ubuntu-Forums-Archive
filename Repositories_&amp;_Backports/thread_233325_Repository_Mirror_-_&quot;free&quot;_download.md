---
title: "Repository Mirror - &quot;free&quot; download"
date: 2006-08-09
forum: Repositories &amp; Backports
---

### Post by najevi on 2006-08-09
Can you offer advice on achieving the following goal subject to the limitation specified:

GOAL: package installs that don't count toward my ISP's monthly data download quota.  

LIMITATION: in Australia at least, many ISP's shape bandwidth (i.e. throttle downstream data rate) after some monthly limit on downloads. In my case it is 10GB/month. I suspect I am not alone.  

OPTIONS: *as I currently see them*[LIST=1]
[*]Advise my ISP how to provide (and maintain) a repository mirror.
[*]Point my ISP to an officially-recognised set of files that allow me to create a repository mirror on my LAN
[*]order a set of DVD's of the repository contents
[*]something else that I haven't thought of[/LIST]In the long run option 1) is my preference however for that to work I'd need to refer my ISP to a recognized & qualified person within the ubuntu community.

Google shows up at least one company that sells a set of DVD's that might suit option 3) above. [SIZE=2][Ubuntu 6.06 LTS Complete]("http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1113&zenid=7afmkrsvtgfugshugbocoigj15")
[/SIZE]
_That leaves Option 2_:

Searching this forum I find a few promising threads describing how to create a local mirror of the repositories.[LIST]
[*][http://www.ubuntuforums.org/showpost.php?p=1312152](http://www.ubuntuforums.org/showpost.php?p=1312152)
[*][http://www.ubuntuforums.org/showpost.php?p=1192639](http://www.ubuntuforums.org/showpost.php?p=1192639)
[*][http://www.ubuntuforums.org/showpost.php?p=219743]("http://www.ubuntuforums.org/#%20http://www.ubuntuforums.org/showpost.php?p=219743")[/LIST]either by download, file-sharing or purchase.

Searching archive.ubuntu.com I find what might be a suitable source for the files refered to in 2) above. viz. [http://archive.ubuntu.com/ubuntu/dists/dapper-updates](http://archive.ubuntu.com/ubuntu/dists/dapper-updates)
subdirectories main, multiverse, restricted & universe

My ISP is willing to host any file that I can specify a legitimate source for. Customer downloads of that file will not count toward a customer's monthly quota. So what I need from informed users at this forum is a list of URL's pointing to the files that comprise the 12GB or so complete repository. 

To help limit scope I care about release=Dapper Drake
& architecture=i386; although to be of service to the widest circle of fellow customers of the same ISP, specifying all architectures might be wise.

The Australian ISP in question is BigPond and, to it's credit, it already hosts 
ubuntu-6.06-alternate-i386.iso &
ubuntuplus-dapper_2006-06-07.iso ([http://www.ubuntuforums.org/showpost.php?p=1063510](http://www.ubuntuforums.org/showpost.php?p=1063510))

Thank you for considering this request. I hope that the answer(s) will help others in a similar situation.

---

### Post by simonn on 2006-08-09
> 
4. something else that I haven't thought of


Move to iinet. Up to 21Mbit download (I get ~20Mbit) / 1Mbit upload, 10Gb peak + 10Gb off-peak shaped to 64kbit for AU$49.95/month (+ ~AU$35 for phone though).

Everything on ftp.iinet.com.au free, including Ubuntu mirror (repos and isos), redhat, debian, knoppix etc.

---

### Post by najevi on 2006-08-10
> **simonn said:**
> Move to iinet. Up to 21Mbit download (I get ~20Mbit) / 1Mbit upload, 10Gb peak + 10Gb off-peak shaped to 64kbit for AU$49.95/month (+ ~AU$35 for phone though).

Everything on ftp.iinet.com.au free, including Ubuntu mirror (repos and isos), redhat, debian, knoppix etc.

Yes iinet is certainly an appealing alternative to BigPond and may well be where I move to in December when my 2 year contract expires. 

The repository files at ftp.iinet.com.au look to be comprehensive. Do you simply point Synaptic/aptget to:
[ftp://ftp.iinet.com.au/linux/ubuntu/dists/dapper-updates](ftp://ftp.iinet.com.au/linux/ubuntu/dists/dapper-updates)
[ftp://ftp.iinet.com.au/linux/ubuntu/dists/dapper-security](ftp://ftp.iinet.com.au/linux/ubuntu/dists/dapper-security)
etc.

If so then persuading BigPond to mirror the repositories might not be as involved as I imagined.

---

### Post by najevi on 2006-08-10
In the interest of getting closure on option 2, let me ask one _very specific question_ for the repository gurus browsing this forum: 

I have read the [debmirror manpage]("http://manpages.debian.net/cgi-bin/display_man.cgi?id=833186a51350ae8f340096c3c5df3d3b&format=html") and it seems that the command line ```
debmirror --nosource --host=archive.ubuntu.com --root=ubuntu/ 
 --dist=dapper --section=main,universe,restricted,multiverse --arch=i386 ./mirror
``` will very tidily create a local mirror of the specified sections of the repository.

My understanding of the four repository sections/components (main, universe, restricted and multiverse) is limited to what I can read at Wikipedia ([Package_classification_and_support]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#Package_classification_and_support")) and from that it appears to me that all but the multiverse section is freely redistributable.[LIST]
[*]**For each of the 4 sections (main, universe, restricted and multiverse) and from both a public and local(private) file hosting perspective are all of these files made available (*and therefore redistributable*) under something similar to the Debian Free Software License?**[/LIST]

---

### Post by najevi on 2006-08-11
I found a helpful overview of repositories (for a std Debian distribution) at 
[http://www.debian.org/doc/manuals/repository-howto/](http://www.debian.org/doc/manuals/repository-howto/) written by *Aaron Isotton.*
It helped me to understand the repository heirarchy and appreciate what a **pool **is and what purpose the **Packages.gz**, **Sources.gz** and **Release **files serve. 

I can now see that the .deb files are located under archive.ubuntu.com/ubuntu/pool 
It is also clear that this pool includes files from all architectures.

If someone has done (*or has ready-access to do*) a ```
debmirror --nosource --host=archive.ubuntu.com --root=ubuntu/ 
 --dist=dapper --section=main,universe,restricted,multiverse --arch=i386
``` to extract a mirror of the i386 + Dapper Drake + [main & universe & restricted & multiverse] 
repositories then please post the [FONT=Courier New]du -s [/FONT]output for these 4 sections of the repository mirror.

---

### Post by we_r_disturbed on 2006-08-11
I messed around with the same post about the debmirror script and for the most part it works.  There were a few changes that I had to make compared to what he did because his sources.list file wasn't correct.
I am in no way saying that my way is correct, but it does work for me so I don't have to redownload the updates every time I reinstall ubuntu.  Here is what I did...

Create a folder on your system to hold the repos...I put mine under /home/username/repos (replace username with your user name)

then...

$ sudo gedit /bin/repoupdate

Then I inserted the following:

#!/bin/bash
cd /home/username/repos
debmirror --nosource -m --passive --host=archive.ubuntulinux.org --root=ubuntu/ --method=ftp --progress --dist=dapper \
--section=main,multiverse,universe --arch=i386 repos/ --ignore-release-gpg
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
sudo dpkg-scansources . /dev/null | gzip -9c > Sources.gz

That takes care of all of his actions at once.  It will download and then create the packages/sources.gz files.  When I first ran it, it took a long time since the files total around 12GB.  That doesn't include the restricted files either, if you want those, just add "restricted" to the list.

Now make your script executable.

sudo chmod +x /bin/repoupdate

Kick off your update by doing:

sudo repoupdate

For your sources.list, you will need to add the following:

deb file:///home/username/repos/repos dapper main universe multiverse
or
deb [http://site](http://site) name or ip address/repos/repos/ dapper main universe multiverse

It all depends on if you are hosting it local or getting it from somewhere else.  I have 2 machines, one hosts it locally and the other gets it thru the ip address.

Like I said, I messed with the other guy's post for a good week before I got it working correctly.  I never got any errors, but when I'd do an install, it would always retreive data from an outside source.  I don't know if this addresses your problem, but if you are following his post it might save you some time.

---

### Post by we_r_disturbed on 2006-08-11
> **najevi said:**
> If someone has done (*or has ready-access to do*) a ```
debmirror --nosource --host=archive.ubuntu.com --root=ubuntu/ 
 --dist=dapper --section=main,universe,restricted,multiverse --arch=i386
``` to extract a mirror of the i386 + Dapper Drake + [main & universe & restricted & multiverse] 
repositories then please post the [FONT=Courier New]du -s [/FONT]output for these 4 sections of the repository mirror.

I took it a bit further and included dapper-updates dapper-backports in my debmirror, and included restricted...adding restricted and dapper-updates/backports only added about 1.3gb worth of downloading.  But as you requested, here is the output.

du -s
12663896        .

Hope that helps

---

### Post by najevi on 2006-08-14
With thanks to **we_r_disturbed** I have the information I need. 
With thanks to **David **(*offline*) my ISP, BigPond, is now hosting a snapsot of the (dapper, i386, nosource, main) repository on the BigPond unmetered content file downloads area (*search [http://files.bigpond.com/index.php](http://files.bigpond.com/index.php) using keywords ***dapper repository**). I hope to persuade David to also post the universe repository section in the near future. The plan is to replace this with a new snapshot periodically.

FYI here is a breakdown of the size of the repository mirrored using:```
debmirror local_mirror_dir --host=archive.ubuntulinux.org --root=ubuntu/
     --**nosource** -m --passive --method=ftp --progress --ignore-release-gpg
     --section=**main,universe,restriced,multiverse** --arch=**i386**
     --dist=**dapper,dapper-backports,dapper-security,dapper-updates**
```[FONT=Courier New]
[/FONT]```
[FONT=Courier New]
_Section_                             _Size in kB_
main                                 2,912,256
restricted                              26,624
universe                             9,318,400
multiverse                             360,448[/FONT]
[FONT=Courier New]
Free     = main+universe          = 12,230,656   97% of  TOTAL
Non-Free = restricted+multiverse  =    387,072    3% of  TOTAL
                           TOTAL  = 12,617,728[/FONT]
```[FONT=Arial Black][COLOR=Blue][SIZE=4]_Is there a better way?_[/SIZE][/COLOR][/FONT]
In the process of investigating all of this I learned about a promising package called [B]
apt-proxy[/B] ([manpage]("http://manpages.debian.net/cgi-bin/display_man.cgi?id=e4c0a7d9244e7ee6ef7dc431df15b4d8&format=html") & [HowTo]("https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo"))  which may prove to be a better* minimalistic *solution 
for a home network ... [I]search for apt-proxy  and you'll find plenty of posts.

enjoy!
[/I]

---

### Post by we_r_disturbed on 2006-08-17
.

---

### Post by airtonix on 2007-04-15
mirror.internode.on.net/pub/ubuntu (proly only accesible by customers)

hehe internode for adelaide has good deals, and a huge linux repository that is not counted to your quota....and they keep it as up to date as possible sometimes i do an apt-get update and upgrade and some of the packages arent all there yet. lol

Also intenode doesnt have those stupid upload quotaing schemes plus they have heaps of other [unmetered content]("http://www.internode.on.net/content/unmetered/") (abc.com.au, oftheworld.tv, etc etc)....

---

