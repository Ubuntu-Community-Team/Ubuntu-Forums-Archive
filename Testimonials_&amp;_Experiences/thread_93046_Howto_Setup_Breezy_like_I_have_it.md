---
title: "Howto: Setup Breezy like I have it"
date: 2005-11-21
forum: Testimonials &amp; Experiences
---

### Post by MarcDM on 2005-11-21
This is less of a howto, and more of a list. A list of computer configurations I currently have, and software I use on them. All of the software mentioned here are either in one of the default Ubuntu/Debian repositories (main,universe,multiverse) or in one of the following repos (these are the lines from /etc/apt/sources.list):
[list]
[*]deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) sarge main
[*]deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) etch main
[*]deb [ftp://mirrors.ibiblio.org/pub/mirrors/blackdown/debian/](ftp://mirrors.ibiblio.org/pub/mirrors/blackdown/debian/) sarge non-free
[/list]
(Java 1.4.2 came from the last one). If I got it from somewhere else, I'll let u know.

So I've been using Ubuntu for a while. I spend all day everyday staring at a screen running Ubuntu; Literally. But I don't write howtos cuz I've had very little time, AND, because I figure that I'm a newbie and know very little. 

I have a little more time now, and I'm a little less of a newbie so.....

In this post, I'm gonna talk about the Debian/Ubuntu boxen I have on/under my desk. Please feel free to ignore me if you want to. 
I'm also happy to answer any questions you might have about something I've mentioned. 
Feel free to point out a better way or to add your config. I might see supmn I like.


**ATHOS** - (Ubuntu 5.10)
Athlon XP 1800, 768MB RAM, 3 x 60GB HDDs, 40/10/32x CDRW, 16x DVD-ROM

This is my main desktop machine. Since my monitor failed 2 weeks ago, I've been accessing it entirely from the 2nd machine in my office, CLASS02. (More on that later). 

Athos uses the stock K7 kernel from the main repositories, esd+alsa for audio. gstreamer+totem for video. So far, I haven't met a video I couldn't play. (I've installed every gstreamer-plugin found in main,universe,multiverse and ftp.nerim repositories.

To handle my music library (all 40+ GB of it), I use [MPD]("http://musicpd.org") and gmpc. mpd was recently moved from Athos to JESTER (more on that later).

For one off tracks, stuff that's not in my library, I use Totem. CDs are played through [goobox]("http://www.gnomefiles.org/app.php?soft_id=531"), and [EasyTag]("http://easytag.sourceforge.net/") edits ID3 tags. (is that what it's called in ogg-vorbis?). Everything else default.

In my daily work, I write code, manage servers, field phone calls, make notes etc....

I program in Python, Java and html using [Eclipse]("http://eclipse.org"). I Downloaded it from their website and installed it into /opt because there seems to be something wrong with the one in the repos.

For my ASP.NET sites, I program in C# using [MonoDevelop]("http://monodevelop.org"), and deloy to my test server (BLACK) running mod_mono.

I used to use [cssed]("http://cssed.sourceforge.net/") to edit CSS files, but the auto-complete feature got annoying. Now I use it for that big CSS Attribute list that it comes with on the right. That's useful.

For a quick mockup using a wysiwyg html editor, I use either [nvu]("http://www.nvu.com/"), OOo or Abiword. I'm not a big fan of wysiwyg html editors anyways. And nvu came from their website. That's also installed in /opt

Mail is handled by Thunderbird ever since Evolution choked on a 3MB file I accidentally selected as a photo for an address book entry. It's not bad. I only wish I could get the panel clock to look at events in Mozilla Calendar. I'll switch back to Evolution eventually though. 

Epiphany is the default browser with the extensions package. I have the tab extension, and the Actions extension. VERY cool. Don't know if I can do it in Firefox, but .....
Firefox is installed, but I use it in web development. That properties box available thru right-click is useful. So is the Javascript error viewer.

Because epiphany phollows the gnome philosophy (:)) of "auto-apply", if you open an html page from your local machine, and edit the html, in another window, the browser updates automatically. Just like wysiwyg. :D

I wish nautilus were more stable. 

[Tomboy]("http://www.beatniksoftware.com/tomboy/") allows me to get away with keeping sloppy notes.

I use Dia to draw diagrams, Inkscape for other kinds of drawing. I'm trying with the gimp, but I still have Macromedia Fireworks installed in wine for making *.gif files. The ones made by the Gimp are HORRIBLE.

**CLASS02**
This "*box*"  is an [NEC Powermate 2000]("http://www.thejournal.com/magazine/vault/A2951.cfm") with no hard drive. It boots [PXES]("http://pxes.sourceforge.net/") thin client, from a CD, and talks to ATHOS via XDMCP.

All audio played here, comes out the soundcard on Athos. But that's cool since they're both on my desk.

Since my [monitor]("http://www.aurora.se/ibm/ibm-t84h.htm") failed, this my new desktop. Still though, access via XDMCP.

**JESTER** Ubuntu Server.
AMD Duron 900, 256MB RAM, 60GB HDD. 

Nothing fancy here. Just an integrated board, with cmipci sound. It runs the Ubuntu 5.10 server with [GnuMp3D]("http://www.gnu.org/software/gnump3d/") to serve music streaming all over the house. It also runs mpd to play music in my office. 

**BLACK** Debian Sarge - Main Server
AMD Athlon 1000Mhz, 512MB RAM, 20GB Hdd (system + programs), 60GB Hdd (data).

Black is my baby. We've been through a lot. I've had her since 1GHz was new.
She runs the stock K7 kernel from the Debian repos. 

```
Apache/2.0.54 (Debian GNU/Linux) mod_jk/1.2.14 
mod_python/3.1.3 Python/2.3.5 PHP/4.3.10-16 Server at black Port 80
```

mod_jk (compiled manually from the [tomcat connectors]("http://tomcat.apache.org/connectors-doc/") source package). [Tomcat]("http://tomcat.apache.org/") is installed in /usr/local (downloaded binary package from their website) and so are Sun's JDKs 1.4.2 and 1.5. mod_mono was also manually compiled.

I have both JDKs installed cuz I use [ Apache Lenya]("http://lenya.apache.org") in tomcat with jre 1.4.2 and 1.5 for everything else (mostly experiments).

I use samba and openldap to manage my small windows domain (6 pcs win2k + winxp). The same ldap server also serves as authentication server for the other Linux machines mentioned above.

My db development, and local database stuff, is handled by posgresql 7.4 and mysql installed on Black. The mysql version is the one I apt-got.

Finally, **Pink** : The veritable firewall on Debian Stable (minus many packages)
Iptables allow everyone email, web and msn-messenger. Everything else is blocked. Oh, and pink allows jester to use bittorrent :D

So there. I've posted. Now this thing can stop telling me that I haven't posted in weeks.

---

### Post by arazaxirelcinellersadolur on 2005-11-21
hi,
i also think like you. i mean that i want to use ubuntu as how as i want to see, feel and use it.
so, meanwhile, i install on my gray laptop ubuntu (5.10) after hoary, and like at hoary, i install only the programs i will use and removed those i never use. then i install my office fonts -some made by me, some converdet to use in Azerbaijani- , then theme configurated. i never use thunderbird and evolution and i removed them also.
as i wrote, my laptop color is gray-colored, and like it, i had configured my theme etc. gray-looking style. only thing i miss to complete is wallpaper which will complete my see-feel-use-love integrated project. so, i saw your attached pic there wallpaper grayed color. could you please send it to me at:
[email]ubuntum@gmail.com[/email]
(ubuntum="my ubuntu" in Azerbaijanian :smile:  )
your respectfully & best regards

---

### Post by nkarasev on 2005-11-23
Hi
Could you, please, explain how you compiled mod_jk?
I am getting error running ./configure:
"checking for C compiler default output file name... configure: error: C compiler cannot create executables". Looking at ../BUILD.txt and ./BUILDING I can figure that there is one option required: something to do with "apxs".
I have no idea of what the heck it is. Also I cannot see anything in /usr/sbin/apxs 
as ../BUILD.txt suggests.

Thanks,
Nikolay

---

### Post by MarcDM on 2005-11-23
[QUOTE=nkarasev]Hi
Could you, please, explain how you compiled mod_jk?
I am getting error running ./configure:
"checking for C compiler default output file name... configure: error: C compiler cannot create executables". Looking at ../BUILD.txt and ./BUILDING I can figure that there is one option required: something to do with "apxs".
I have no idea of what the heck it is. Also I cannot see anything in /usr/sbin/apxs 
as ../BUILD.txt suggests.[/QUOTE]

Well, I'll have to look back @ the server to get the exact instructions, but ...

Make sure you have the following installed :
[list]
[*]apache2-dev
[*]build-essential
[/list]

The first one is what provides the apxs, the 2nd package ensures that you have the essentials to build the package.

----
Hope this helps.

---

### Post by nkarasev on 2005-11-24
Hi,

I have checked and foudnt that there is NO apache2-dev available for my system
(using advanced option of Synaptic Package Manager.)
I did find and install build-essential and this did improve building of mod_jk a bit.
Now, because there is no apache2-dev I am stopped at the following messages from ./configure:
----------------------------------------------
no apxs given
checking for target platform... unix
no apache given
configure: error: Cannot find the WebServer
----------------------------------------------
So where to find apache2-dev?

Thanks,
Nikolay

---

### Post by skwee on 2005-12-03
ubuntu has only mod_jk2 for apache2 which is not developed any more. And there is no apache2-dev in ubuntu. Here is how I got mod_jk working with breezy.  

This guy [http://www.crazysquirrel.com/computing/debian/tomcat55.jspx]("http://www.crazysquirrel.com/computing/debian/tomcat55.jspx") has written a debian howto, that might be usefull.

Install apache2-threaded-dev from ubuntu repository.

Download the connector source jakarta-tomcat-connectors-1.2.15-src.tar.gz from apache.
Unpack and build with
```

cd jk/native
./configure --with-apxs=/usr/bin/apxs2 --with-apach=/etc/apache2
make
make install

```

Here is the additional configuration needed. refer to the official docs for more info
/etc/apache2/mods-available/jk.load
```
LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so
```

/etc/apache2/mods-available/jk.conf
```
<IfModule mod_jk.c>
    JkWorkersFile /etc/apache2/workers.properties
    JkMountFile   /etc/apache2/uriworkermap.properties
    JkLogFile     /var/log/apache2/mod_jk.log
    JkLogLevel    debug 
</IfModule>
```

/etc/apache2/workers.properties
```
worker.list=foo

# Definition for local worker using AJP 1.3
#
worker.foo.type=ajp13
worker.foo.host=localhost
worker.foo.port=8009
worker.foo.cachesize=20
```

/etc/apache2/uriworkermap.properties
```
/tomcat-docs/*=foo
```

---

### Post by skwee on 2006-01-01
Update: It seem's there is now a
  apache2-threaded-dev:D 

You still have to compile and configure mod_jk:???: 

Cheers
Steve

---

### Post by pdaoust on 2006-02-01
**MarcDM**: do you have any pointers, or links to HOWTOs, for getting OpenLDAP to work as a domain authentication server? e.g., do you have Kerberos for authentication, and if so, how do you get Kerberos to talk to OpenLDAP, and what LDAP schema do you use, etc, etc, etc? I'm looking for information primarily in a Linux context, 'cuz I administer a small private school's network, and right now the kids all have one account: 'student'. Not very graceful.

thanks!

---

### Post by MarcDM on 2006-02-01
I'm still not too sure about this kerberos thing. So I go around and change that config on the WinXP boxen so they can login to the domain. 

As for schema....
Each member has the following set of ObjectClass :
inetOrgPerson(structural), posixAccount, shadowAccount and sambaSamAccount

Each of those objectClasses define their own set of required attributes that once available, u should be able to login.

After you install ldap server, install phpldapadmin somewhere and configure it to point to the server you just installed. It's a big help.

Sorry for not posting links and such, but I'm rushing this...
I'll post a more proper response tomorrow... maybe a new thread?

---

