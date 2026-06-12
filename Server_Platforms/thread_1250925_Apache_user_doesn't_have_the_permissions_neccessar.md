---
title: "Apache user doesn't have the permissions neccessary to run cURL, fopen(), and others."
date: 2009-08-27
forum: Server Platforms
---

### Post by XtremeGamer99 on 2009-08-27
Hello,

Alright, first off, I'm not using Ubuntu. I'm using Arch Linux. Now that that's out of the way:

Secondly, much more details about my battle with this server can be found [here]("http://bbs.archlinux.org/viewtopic.php?pid=608735"). below is just the basics of what I've gotten to so far.

Whenever I try to do a cURL function in a PHP page through a web browser, it fails, giving and error about `Couldn't resolve hosts`. However, that same PHP page with the curl functions succeed when run in the terminal, which has lead me to believe that Apache is the culprit (since it fails when being served from the Apache web server).

I finally figured out why. The Apache user, http, doesn't have the permissions necessary to use the cURL, fopen(), and other web-site manipulation functions. I figured this out by making root the Apache server user, which then was able to successfully execute my PHP page from the web browser...

Now what I want to know is how do I fix this. I have no leads as to where to go from here...

Any help?

PS: Sorry if this is the wrong forum, but I figured the Secuirty Discussions people would know more about permissions and whatnot. :P

---

### Post by dk06 on 2009-08-27
looks like you're not the only one w/these issues...have you tried google?

**[http://curl.askapache.com/docs/knownbugs.html](http://curl.askapache.com/docs/knownbugs.html)**

> 

[LIST=1]
[*]**[Re: chunked encoding *problem* ? - error messages from *curl* as well [B]...**]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fmail-archives.apache.org%2Fmod_mbox%2Fcouchdb-dev%2F200906.mbox%2F%253C9E90C585-D3E3-4E29-AD3C-DEB99B86E1B4%40apache.org%253E&ei=ezWWSvP8H4XitgOs3qGQDA&usg=AFQjCNEGzktOvvyv9PrUi1k0p0pACkM_MA&sig2=EuSIE1CcuyJz1Zlp9h7nJg")[/B]

*apache*.org>. Subject, Re: chunked encoding *problem* ? - error messages from *curl* as well as lucene. Date, Tue, 30 Jun 2009 18:47:50 GMT **...**
mail-archives.**apache**.org/.../%3C9E90C585-D3E3-4E29-AD3C-DEB99B86E1B4@**apache**.org%3E - [Cached]("http://74.125.155.132/search?q=cache:hTiWmbo1cbUJ:mail-archives.apache.org/mod_mbox/couchdb-dev/200906.mbox/%253C9E90C585-D3E3-4E29-AD3C-DEB99B86E1B4%40apache.org%253E+cURL+and+apache+problem&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:mail-archives.apache.org/mod_mbox/couchdb-dev/200906.mbox/%253C9E90C585-D3E3-4E29-AD3C-DEB99B86E1B4%40apache.org%253E") -
[*]**[Re: chunked encoding *problem* ? - error messages from *curl* as well [B]...**]("http://mail-archives.apache.org/mod_mbox/couchdb-dev/200907.mbox/%3CED26000E-C9B8-48C9-A0BF-ED252CCF9157@apache.org%3E")[/B]

*apache*.org>. Subject, Re: chunked encoding *problem* ? - error messages from *curl* as well as lucene. Date, Wed, 01 Jul 2009 16:41:37 GMT **...**
mail-archives.**apache**.org/.../%3CED26000E-C9B8-48C9-A0BF-ED252CCF9157@**apache**.org%3E - [Cached]("http://74.125.155.132/search?q=cache:flKTA-EQZggJ:mail-archives.apache.org/mod_mbox/couchdb-dev/200907.mbox/%253CED26000E-C9B8-48C9-A0BF-ED252CCF9157%40apache.org%253E+cURL+and+apache+problem&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:mail-archives.apache.org/mod_mbox/couchdb-dev/200907.mbox/%253CED26000E-C9B8-48C9-A0BF-ED252CCF9157%40apache.org%253E") - 
[Show more results from mail-archives.apache.org]("http://www.google.com/search?q=cURL+and+apache+problem&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#")
[*]**[*cURL* with PHP and *Apache* on Windows]("http://www.tonyspencer.com/2003/10/22/curl-with-php-and-apache-on-windows/")**

*cURL* with PHP and *Apache* on Windows · Code October 22nd, 2003. Setting up *cURL* my linux server it was no *problem* at all,  but I had a heck of a time getting **...**
[www.tonyspencer.com/.../]("http://www.tonyspencer.com/.../")**curl**-with-php-and-**apache**-on-windows/ - [Cached]("http://74.125.155.132/search?q=cache:PyAJaAZKohYJ:www.tonyspencer.com/2003/10/22/curl-with-php-and-apache-on-windows/+cURL+and+apache+problem&cd=3&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:www.tonyspencer.com/2003/10/22/curl-with-php-and-apache-on-windows/") -
[*]**[installing php/*curl* on *Apache problem*: msg#00035]("http://www.google.com/url?sa=t&source=web&ct=res&cd=4&url=http%3A%2F%2Fosdir.com%2Fml%2Fweb.curl.php%2F2003-07%2Fmsg00035.html&ei=ezWWSvP8H4XitgOs3qGQDA&usg=AFQjCNG9M4lu-NMPeSLZetekEmSO3me8ZQ&sig2=UYKsphuq0T8ildIpYCcs6A")**

I enabled *curl* in php.ini (extension=php_curl.dll), and when I restarted *Apache* I am getting a wierd error message pop-up "The procedure entry point **...**
osdir.com/ml/web.**curl**.php/2003-07/msg00035.html - [Cached]("http://74.125.155.132/search?q=cache:0xx2byncnYYJ:osdir.com/ml/web.curl.php/2003-07/msg00035.html+cURL+and+apache+problem&cd=4&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:osdir.com/ml/web.curl.php/2003-07/msg00035.html") -
[*]**['installing php/*curl* on *Apache problem*' - MARC]("http://marc.info/?l=curl-and-php&m=105954681806421&w=2")**

[prev in thread] [next in thread] List: *curl*-and-php Subject: installing  php/*curl* on *Apache problem* From: "Felix Rabinovich" <felix () rabinovich ! org> **...**
marc.info/?l=**curl**-and-php&m=105954681806421&w=2 - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:marc.info/%3Fl%3Dcurl-and-php%26m%3D105954681806421%26w%3D2") -
[*]**[*Curl*: installing php/*curl* on *Apache problem*]("http://curl.haxx.se/mail/curlphp-2003-07/0035.html")**

installing php/*curl* on *Apache problem*. This message : [ Message body ] [ More options ]; Related messages : [ Next message ] [ Previous message ]  **...**
**curl**.haxx.se/mail/**curl**php-2003-07/0035.html - [Cached]("http://74.125.155.132/search?q=cache:taDUAot9_lAJ:curl.haxx.se/mail/curlphp-2003-07/0035.html+cURL+and+apache+problem&cd=6&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:curl.haxx.se/mail/curlphp-2003-07/0035.html") -
[*]**[Arch Linux Forums / *cURL*, PHP, *Apache*, Insanity!]("http://bbs.archlinux.org/viewtopic.php?pid=608122")**

3 posts - 2 authors - Last post: 5 days ago
tl;dr: *cURL* doesn't work when it's used in a PHP application and **...** An *Apache problem*? Below, I've included  some  network information that **...**
bbs.archlinux.org/viewtopic.php?pid=608122 - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:bbs.archlinux.org/viewtopic.php%3Fpid%3D608122") -
[*]**[[#COUCHDB-387] *curl*: (56) Received *problem* 2 in the chunky parser [B]...**]("http://issues.apache.org/jira/browse/COUCHDB-387")[/B]

*Curl* returned this at the end of the output: ---- *curl*: (56) Received *problem* 2 in the chunky parser ---- After changing the ë to a plain e this *problem* **...**
issues.**apache**.org/jira/browse/COUCHDB-387 - [Cached]("http://74.125.155.132/search?q=cache:bc6rioc1t_kJ:issues.apache.org/jira/browse/COUCHDB-387+cURL+and+apache+problem&cd=8&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:issues.apache.org/jira/browse/COUCHDB-387") -
[*]**[*Apache* 2, PHP 5.1.4 And *cURL*]("http://www.astahost.com/info.php/Apache-2-Php-514-Curl_t12464.html")**

Jun 19, 2006 **...** But I still have *problems* using the *curl* libraryof functions if I go through *Apache*. Using the php compiler from command line works just **...**
[www.astahost.com/info.../]("http://www.astahost.com/info.../")**Apache**-2-Php-514-**Curl**_t12464.html - [Cached]("http://74.125.155.132/search?q=cache:wuq6KqWiqdwJ:www.astahost.com/info.php/Apache-2-Php-514-Curl_t12464.html+cURL+and+apache+problem&cd=9&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:www.astahost.com/info.php/Apache-2-Php-514-Curl_t12464.html") -
[*]**[*cURL* - Known Bugs]("http://curl.askapache.com/docs/knownbugs.html")**

May 11, 2009 **...** This is the document 'docs/KNOWN_BUGS' from the *curl* release archive. These are *problems* known to exist at the time of this release. **...**
**curl**.ask**apache**.com/docs/knownbugs.html - [Cached]("http://74.125.155.132/search?q=cache:5As0CA4iudMJ:curl.askapache.com/docs/knownbugs.html+cURL+and+apache+problem&cd=10&hl=en&ct=clnk&gl=us&client=firefox-a") - [Similar]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=5oZ&q=related:curl.askapache.com/docs/knownbugs.html") -
[/LIST]


---

### Post by XtremeGamer99 on 2009-08-27
> **dk06 said:**
> looks like you're not the only one w/these issues...have you tried google?

**[http://curl.askapache.com/docs/knownbugs.html](http://curl.askapache.com/docs/knownbugs.html)**

Admittedly, I haven't done an extensive search since I discovered that Apache didn't have the permissions. But I did search Google as if it was a Bible trying to figure out why cURL wasn't working in the first place. The results I got were mostly inconclusive or very much outdated... The searching I *did* do in respect to Apache's permissions only turned up irrelevant things like making sure your web directory has the correct chmod for the server to read. 

Thanks for the links, I'll look into them. =) What search term did you use specifically?

EDIT: Also, one of those search results are mine from the Arch Linux forums. =P

EDIT 2: Upon reviewing the links that you posted, most of them are either irrelevant to my problem (or I'm not reading them right -- mailing lists tend to be a little *to* technical for me to follow), deal with the installation of cURL (which isn't my problem), or deal with Windows instead of Linux (I have no idea if the windows versions are much different). Thanks for the help, though, I appreciate it. =)

---

### Post by dk06 on 2009-08-27
no worries, I just notice a lot of posters could save time by checking google

(posting in forums can be really helpful too I've just found google to be an excellent resource in addition to forums)

> cURL and apache problemHave a good one & good luck!

edit:

I'll take another look, thought I saw something similar

---

### Post by XtremeGamer99 on 2009-08-27
> **dk06 said:**
> no worries, I just notice a lot of posters could save time by checking google

(posting in forums can be really helpful too I've just found google to be an excellent resource in addition to forums)

Have a good one & good luck!

edit:

I'll take another look, thought I saw something similar

The similar one is probably my post on Arch. xD

I will also continue searching for this. It's been kicking me in the rump for the past week now and I want it solved. :)

---

### Post by dk06 on 2009-08-27
[http://www.astahost.com/info.php/Apache-2-Php-514-Curl_t12464.html](http://www.astahost.com/info.php/Apache-2-Php-514-Curl_t12464.html)
> 
I have been running PHP 5.1.4 and Apache 2.2.2 with the PHP 5.2.0 developement phpapache2_2.dll module. I recently installed CURL with php. **Now if I run php from the command line, I can use the CURL functions, but not from a webpage through Apache**. Also, phpinfo() returns nothing on CURL. I am running Windows XP SP2 and installed PHP manually via the zipped binaries. I really need CURL to work through a webpage and would appreciate any help I can get.
[http://curl.haxx.se/mail/lib-2009-08/0253.html](http://curl.haxx.se/mail/lib-2009-08/0253.html)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478864](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478864)


_**possible fix**_:

[http://thebigbyte.blogspot.com/2009/08/how-to-enable-curl-in-php-on-linux.html](http://thebigbyte.blogspot.com/2009/08/how-to-enable-curl-in-php-on-linux.html)

> 
** [How To Enable Curl in PHP on Linux]("http://thebigbyte.blogspot.com/2009/08/how-to-enable-curl-in-php-on-linux.html") **

    
    To enable PHP Curl support on Linux with apache 2:

$ sudo apt-get install php5-curl

Or do it manually (compiling sources):
[http://au2.php.net/manual/en/curl.installation.php](http://au2.php.net/manual/en/curl.installation.php) 
[http://curl.haxx.se/libcurl/php/install.html](http://curl.haxx.se/libcurl/php/install.html)
[http://www.wallpaperama.com/forums/how-to-find-out-if-php-is-compiled-with-curl-extension-installed-enabled-t1576.html](http://www.wallpaperama.com/forums/how-to-find-out-if-php-is-compiled-with-curl-extension-installed-enabled-t1576.html)  ** **

  [ ]("http://thebigbyte.blogspot.com/2009/08/how-to-enable-curl-in-php-on-linux.html") 
 
  					This entry was written by  					 David   					and posted on  					Monday, August 03, 2009 						and filed under  					 [ apache ]("http://thebigbyte.blogspot.com/search/label/apache") , [ linux ]("http://thebigbyte.blogspot.com/search/label/linux") , [ open source ]("http://thebigbyte.blogspot.com/search/label/open%20source") , [ php ]("http://thebigbyte.blogspot.com/search/label/php")  					Bookmark the  					[ 						permalink 					]("http://thebigbyte.blogspot.com/2009/08/how-to-enable-curl-in-php-on-linux.html").  					Follow any comments here with the  					[ 						RSS feed for this post 					]("http://thebigbyte.blogspot.com/feeds/6969308757105329189/comments/default"). 					[ 						Post a comment 					]("http://thebigbyte.blogspot.com/2009/08/how-to-enable-curl-in-php-on-linux.html#comments") (  					[ 						in a new window 					]("https://www.blogger.com/comment.g?blogID=203080733111610229&postID=6969308757105329189&isPopup=true") ) 					


---

### Post by XtremeGamer99 on 2009-08-27
> **dk06 said:**
> [http://www.astahost.com/info.php/Apache-2-Php-514-Curl_t12464.html](http://www.astahost.com/info.php/Apache-2-Php-514-Curl_t12464.html)
[http://curl.haxx.se/mail/lib-2009-08/0253.html](http://curl.haxx.se/mail/lib-2009-08/0253.html)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478864](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478864)


_**possible fix**_:

[http://thebigbyte.blogspot.com/2009/08/how-to-enable-curl-in-php-on-linux.html](http://thebigbyte.blogspot.com/2009/08/how-to-enable-curl-in-php-on-linux.html)

Thank you for looking into this. I stumbled on a few of these pages as well. But unfortunately, most of these aren't relevant or don't address my issue as I have it.

To clarify - cURL works. No doubt about it. I've tried it on the terminal, I've tried it through PHP scripts... there isn't a thing wrong with cURL. However, there *is* a problem with Apache and the web server user not have the proper permissions to perform cURL and other URL operations (for whatever reason). I'd like to find out why and how to fix that, if there is a way. x_x

Again, thanks for your help. I appreciate all the help I can get; otherwise, I'd throw the machine out the window. :P

---

### Post by dk06 on 2009-08-27
> **XtremeGamer99 said:**
> Thank you for looking into this. I stumbled on a few of these pages as well. But unfortunately, most of these aren't relevant or don't address my issue as I have it.

To clarify - cURL works. No doubt about it. I've tried it on the terminal, I've tried it through PHP scripts... there isn't a thing wrong with cURL. However, there *is* a problem with Apache and the web server user not have the proper permissions to perform cURL and other URL operations (for whatever reason). I'd like to find out why and how to fix that, if there is a way. x_x

Again, thanks for your help. I appreciate all the help I can get; otherwise, I'd throw the machine out the window. :P

I'm not running apache but if you go into your users/groups & edit the permissions (add curl to the apache user) would that work

again, I don't have apache or curl but I've had a lot of program user/groups that I've needed to edit the permissions on for other things in order for them to work properly.

can't think of any other potential solutions, and you're right...it's a tough one to search in google

---

### Post by XtremeGamer99 on 2009-08-27
> **dk06 said:**
> I'm not running apache but if you go into your users/groups & edit the permissions (add curl to the apache user) would that work

again, I don't have apache or curl but I've had a lot of program user/groups that I've needed to edit the permissions on for other things in order for them to work properly.

can't think of any other potential solutions, and you're right...it's a tough one to search in google

Sorry if this is a newbish question, but how would I add the cuRL program to the http user? 

I'll continue to search. =P

---

### Post by dk06 on 2009-08-27
> **XtremeGamer99 said:**
> Sorry if this is a newbish question, but how would I add the cuRL program to the http user? 

I'll continue to search. =P


I have apps like Splunk, OSSEC,...etc... that actually have a username, I was assuming maybe Apache had one and apps like VMware & Virtualbox, you need to edit the permissions on your users and add the VMware/VBox group premissions to the user


I don't run a web server so I don't know if that applies to Apache or cURL, but it was just a thought

---

### Post by cariboo on 2009-08-27
The Debian way is to use root and www-data in /var/www, You'll have to check what groups Arch uses. the easiest way is to open a terminal and type:

```
ls -l
```

the above command will give you a long  listing which includes permissions and owner ship.

To add someone to a group, in a terminal type:

```
gpasswd -a <user> <group>
```

It is kind of hard to suggest what you should do as Debian/Ubuntu and Arch do things differently as far as apache2 goes.

---

### Post by XtremeGamer99 on 2009-08-27
> **cariboo907 said:**
> The Debian way is to use root and www-data in /var/www, You'll have to check what groups Arch uses. the easiest way is to open a terminal and type:

```
ls -l
```

the above command will give you a long  listing which includes permissions and owner ship.

To add someone to a group, in a terminal type:

```
gpasswd -a <user> <group>
```

It is kind of hard to suggest what you should do as Debian/Ubuntu and Arch do things differently as far as apache2 goes.

You seem to suggest that there is a problem with the files permission instead of Apache's permissions. That's not really the problem... The files are stored in my personal home directory under /home/[username]/public_html/[site]. All files are owned by me and my group, except for files and directories that need to be written by Apache (they are either assigned to the http group or are given 777 permissions). That said, it's not a problem the PHP file's permissions, but with the http user's (Apache) permissions not being able to execute cURL, fopen, etc when trying to fetch data from a remote site...

---

### Post by cariboo on 2009-08-27
This really isn't a security question, I"m moving this thread to Server platforms, as you will probably get the help you need there to solve your problem.

---

