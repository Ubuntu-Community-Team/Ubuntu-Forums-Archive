---
title: "Easiest way to meld multiple large huge hosts files (block unwanted parasitic sites)"
date: 2011-11-11
forum: Security
---

### Post by rocksockdoc on 2011-11-11
Can you suggest improvements to this process of maintaining a large hosts file?

When I find an objectionable site (advertisement, redirect, flash content, etc.) I simply add the domain to my hosts file and never have to see that content again.

But every few months, I find a few more unwanted parasites slipping through, so I pick up a [new (huge) hosts file]("http://winhelp2002.mvps.org/hosts.txt"), from, say:
```
http://winhelp2002.mvps.org/hosts.htm
```

What I do is save the hosts.txt file to /tmp/hosts.txt and then strip out all but the redirects (remove double spaces, remove comments, & remove the localhost line)
```
http://winhelp2002.mvps.org/hosts.txt
grep -v \# hosts.txt | sed -e 's/  / /g' | grep -v 127.0.0.1 localhost\$ | sort -u >> /etc/hosts

NOTE: The sed is removing redundant spaces so it's consistent with my existing hosts file.

```My first problem is getting the syntax right for the removal of the localhosts line (I actually have to delete that one line manually because some of the valid lines to keep also have localhosts in the domain name).

Then, I try to cull out duplicates, using:
```
sort -u /etc/hosts -o /etc/hosts

```Unfortunately, that process moves the localhost and other top-level lines to a lower level which I then have to manually bring back to the top to keep a semblance of the original hosts order.

```

127.0.0.1 machine localhost.localdomain localhost
127.0.1.1 machine
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
# begin parasitic blocks

```This process works - but it could use an improvement.

Any ideas?

---

### Post by HermanAB on 2011-11-13
The easiest way is to give up and use DynDNS or OpenDNS instead of trying to do it yourself.

---

### Post by rocksockdoc on 2011-11-20
> **HermanAB said:**
> The easiest way is to give up and use DynDNS or OpenDNS instead of trying to do it yourself.

I guess I asked the wrong question ... because I was just hoping to find an easier way to merge multiple huge files culling out the duplicates ... 

But, since both suggestions are unknown to me, looking up what DynDNS & OpenDNS are (in Wikipedia), I find:

[LIST]
[*][According to Wikipedia, DynDNS]("http://en.wikipedia.org/wiki/DynDNS") apparently provides two free services
[LIST]
[*]It regularly changes your apparent IP address
[*]It also seems to have a poorly defined Internet content filtering service
[/LIST]
[*][According to Wikipedia, OpenDNS]("http://en.wikipedia.org/wiki/OpenDNS") apparently provides ad-supported services
[LIST]
[*]It seems to do free content filtering but it's supported by advertisements
[*]These ads seem to show up in strange places (when undecipherable URLs are entered???)
[/LIST]
[/LIST]
The whole point is to easily eliminate millions of advertisements with a single hosts file, so there doesn't appear to be much sense in further exploring OpenDNS (because it seems to be supported by advertisements - which is the entire point to eliminate!).

But the DynDNS service does seem intriguing at first glance. I actually like BOTH things it does (i.e., change your IP address regularly and perform some type of content filtering, whatever that means to it).

I'll explore DynDNS further - but what I was 'really' looking for were simple UNIX commands to cull out duplicates from huge merged files.

---

### Post by Jonathan L on 2011-11-21
> simple UNIX commands to cull out duplicates from huge merged files.Hi Rocksockdoc

I'll confess I'd not seen this technique before: what a great way to deal with some of the spam!

How about this to address your management problems:

Make a file /etc/hosts.real with your real things, and a directory /etc/hosts.d to contain the files you get from others.  Just put the files you download in there, and any that you maintain yourself.

The script below then creates a new hosts file for you in /etc which looks like
```
# hosts file made Mon Nov 21 16:18:44 GMT 2011
# contents of /tmp/hosts.real
127.0.0.1    localhost
127.0.1.1    laptop
192.168.0.32    myserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
# contents of /tmp/hosts.d/*
#  total 1200
#  -rw-rw-r-- 1 jonathan jonathan 612606 2011-11-21 12:37 hosts2.txt
#  -rw-rw-r-- 1 jonathan jonathan 612606 2011-10-13 18:49 hosts.txt
127.0.0.1                             ads.7days.ae
127.0.0.1                             ads.angop.ao
127.0.0.1              smartad.mercadolibre.com.ar
[14,000 more...]
```is that what you were looking for?  The script is unecessarily elegant regarding the sorting (so that bad.spam.com is next to awful.spam.com, not badman.com), but perhaps you'll enjoy that!

You could have a cronjob do wget to pick up [http://winhelp2002.mvps.org/hosts.txt](http://winhelp2002.mvps.org/hosts.txt) periodically and rebuild your /etc/hosts, or just run it manually when you like.  As listed here it works on /tmp/hosts.d, /tmp/hosts.real and produces /tmp/hosts: edit the red bit to get it to do it for real (which will probably require root permission to overwrite /etc/hosts and create /etc/hosts.new)
```
#!/bin/sh

set -e
dir=[COLOR=Red]/tmp[/COLOR]

echo "# hosts file made `date`" > $dir/hosts.new
echo "# contents of $dir/hosts.real" >> $dir/hosts.new

cat $dir/hosts.real >> $dir/hosts.new

echo "# contents of $dir/hosts.d/*" >> $dir/hosts.new
ls -l $dir/hosts.d | awk '{print "# ", $0;}' >> $dir/hosts.new

# tr to lowercase
# remove any cr in the files
# delete comments and trailing newlines
# lose line which is 'lowercase'
# print domain backwards (www.example.com -> com.example.www)
# lose extra trailing dot
# sort and uniq
# backwards back to normal order (www.example.com)
# lose extra trailing dot
# print with address, right justified
# into the file
#
cat $dir/hosts.d/* \
| tr A-Z a-z \
| tr -d '\r' \
| awk '{gsub("#.*$", ""); gsub(" *$",""); if (NF==2) {print $2;}}' \
| grep -v '^localhost$' \
| awk -F. '{for(i=NF;i>0;--i){printf("%s.",$i);}{printf("\n");}}' \
| sed 's/\.$//' \
| sort | uniq  \
| awk -F. '{for(i=NF;i>0;--i){printf("%s.",$i);}{printf("\n");}}' \
| sed 's/\.$//' \
| awk '{printf("127.0.0.1 %40s\n", $1);}' \
>> $dir/hosts.new

mv $dir/hosts.new $dir/hosts

# end
```Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by bodhi.zazen on 2011-11-21
> **Jonathan L said:**
> Hi Rocksockdoc

I'll confess I'd not seen this technique before: what a great way to deal with some of the spam!

How about this to address your management problems:

Make a file /etc/hosts.real with your real things, and a directory /etc/hosts.d to contain the files you get from others.  Just put the files you download in there, and any that you maintain yourself.

The script below then creates a new hosts file for you in /etc which looks like
```
| sort | uniq  \
```Hope that's helpful.

Kind regards,
Jonathan.

I did not critique your entire script, but no need to pipe sort to uniq , just use sort -u . See man sort for details.

I suspect you could simplify the script further as there is little need to pipe cat to awk either. Depending on the format of your source hosts file you can probably do all this with a one liner.

---

### Post by Jonathan L on 2011-11-21
Thanks for your comments Bodhi:

>  but no need to X / could simplify the script / you can probably do all this with a one liner.Indeed, of course.  A script with the same overall effect (but different sort order and formatting) is:
```
dir=/tmp

(cat $dir/hosts.real
awk '{gsub("\r",""); gsub("#.*$", ""); gsub(" *$",""); if  ((NF==2)&&($2!="localhost")) {print "127.0.0.1", tolower($2);}}'  $dir/hosts.d/* | sort -u) > $dir/hosts.new && mv  $dir/hosts.new $dir/hosts

```Personally I find it much better to have a style which is more modular and easier to debug than one which is more "efficient" for the computer.  In particular, the "cat-at-top" style allows you to insert
```
| tee tmpfile \
```in between any line, or add 'tr' somewhere or another sort or another awk.  (As I'm sure some readers know and some don't: awk will take any number of files, tr doesn't take filenames, and some versions of sort don't allow -u.)  If you use this tyle of "big modular pipeline" you can build things up quickly, adding short one-liners to solve each part of the puzzle.  In this particular case, some of the tr was added late, to fix the spurious carriage returns, and it's irritating to have move the filenames around.

And again, I was trying to make something intelligible for rocksocdoc to get some ideas from.

Just a matter of what I've found works well over the years: but to each their own.

Kind regards
Jonathan.

---

### Post by bodhi.zazen on 2011-11-21
Nice one liner, and thank you for your explanations, they are nice

I like the idea of being modular, and I was not trying to be critical, sorry if I came across that way.

I used to :

cat | grep 
sort | uniq 

awk similarly a powerful tool ;)

---

### Post by emiller12345 on 2011-11-22
> **Jonathan L said:**
> 
```

cat $dir/hosts.d/* \
| tr A-Z a-z \
| tr -d '\r' \
| awk '{gsub("#.*$", ""); gsub(" *$",""); if (NF==2) {print $2;}}' \
| grep -v '^localhost$' \
| awk -F. '{for(i=NF;i>0;--i){printf("%s.",$i);}{printf("\n");}}' \
| sed 's/\.$//' \
| sort | uniq  \
| awk -F. '{for(i=NF;i>0;--i){printf("%s.",$i);}{printf("\n");}}' \
| sed 's/\.$//' \
| awk '{printf("127.0.0.1 %40s\n", $1);}' \
>> $dir/hosts.new

```

try this addition, it sorts keeping like-domains together
```

| tr A-Z a-z \
| tr -d '\r' \
| awk '{gsub("#.*$", ""); gsub(" *$",""); if (NF==2) {print $2;}}' \
| grep -v '^localhost$' \
| awk -F. '{for(i=NF;i>0;--i){printf("%s.",$i);}{printf("\n");}}' \
| sed 's/\.$//' \
**| awk -F\. '{ORS=""; for(I=NF; I>=1;I--){print $I; if(I!=1){print "."}}; print "\n"}' \**
| sort | uniq  \
**| awk -F\. '{ORS=""; for(I=NF; I>=1;I--){print $I; if(I!=1){print "."}}; print "\n"}' \**
| awk -F. '{for(i=NF;i>0;--i){printf("%s.",$i);}{printf("\n");}}' \
| sed 's/\.$//' \
| awk '{printf("127.0.0.1 %40s\n", $1);}' \

```
[COLOR=Red]Disregard this code... blah [/COLOR]

---

### Post by Jonathan L on 2011-11-22
HI Emiller

Thanks for your suggestion, but I think you'll find that the original script already sorted the domains from the right (ie, all the com together, all the uk together etc), which is the purpose (as noted in the comments) of the two awks around the sort; your additions nullify that effect.

For what it's worth: I recommend printf over print and echo in various languages.  The main reason for this is portability and flexibility, for the price of a bit of learning.  As C, perl, php, awk, java and many other languages have printf, you can learn it once and use it in lots of places.

Rocksockdoc: hope you're finding what you need in this thread.

Kind regards,
Jonathan.

---

### Post by emiller12345 on 2011-11-23
> **Jonathan L said:**
> HI Emiller

Thanks for your suggestion, but I think you'll find that the original script already sorted the domains from the right (ie, all the com together, all the uk together etc), which is the purpose (as noted in the comments) of the two awks around the sort; your additions nullify that effect.

For what it's worth: I recommend printf over print and echo in various languages.  The main reason for this is portability and flexibility, for the price of a bit of learning.  As C, perl, php, awk, java and many other languages have printf, you can learn it once and use it in lots of places.

Rocksockdoc: hope you're finding what you need in this thread.

Kind regards,
Jonathan.
Ah yes, I see now.  Don't know how I missed that before. As I was testing out your script I thought that it was sorting the urls from left to right (normal sort). my apologies.

---

### Post by HermanAB on 2011-11-24
BTW, instead of reading a Wikipedia article on DynDNS, you should rather go to the DynDNS web site and see for yourself.  It is a pretty good service.  I have configured it for use on the public computers at a number of family centres.

IMHO, trying to filter out internet cruft is a huge waste of time, best done by a large service company like DynDNS.  It is not something that a single person can do properly.

---

### Post by unspawn on 2011-11-24
> **rocksockdoc said:**
> Can you suggest improvements to this process of maintaining a large hosts file?
Sure: don't ;-p Blocking ads and trackers is a Sisyphus task. Using /etc/hosts is crude because it is a static listing and *only deals with resolving domain names*. And by using an external block list you let the creator define what is bad or unwanted. Depending on your browsing habits ninety nine percent of its contents may not even be of any use to you.

To gauge what such a kludge really is worth try explaining how you would block these using /etc/hosts:
 - incrementally update your block list,
 - block ad-tracking cookies,
 - block ads residing in a path on the same server you visit,
 - block ads from a host name of which the domain name is the same as the server you visit,
 - block ads on the same server you visit presented through Javascript or Flash,
 - block ads by host or path substring match,
 - block only web bugs,
 - block ads server over HTTPS,
 - set session-only cookies for a range of sites,
 - selectively block pop-ups, refresh-tags and redirects,
 - keep images with specific sizes from displaying,
 - block visiting domains based on content,

Well actually you don't need to try because you can't. If you don't like OpenDNS or Google DNS then you could use a persistent caching DNS server like Pdns. It speeds up lookups, allows you to block IP addresses using /etc/hosts-style files and change what's blocked or not dynamically. Add to that a proxy like Privoxy because filtering is the single most efficient way of blocking ads and trackers. It can do everything /etc/hosts can't and besides, every time anyone suggests using /etc/hosts a puppy dies ;-p

---

### Post by rocksockdoc on 2012-01-06
I just came back here to remember how to update my hosts file and merge & delete duplicates.

> **unspawn said:**
> Blocking ads and trackers is a Sisyphus task. Using /etc/hosts is crude because it is a static listing and *only deals with resolving domain names*.

While this statement is inherently true, the statement is too black & white & may discourage others. 

Personally, my 32K line long /etc/hosts file is not any bother whatsoever to manage (in practice, I only update it en masse whenever I feel like it, which turns out to be about once every few months).

In addition, whenever I go to a repeat site (e.g., the NY Times, Wall Street Journal, etc.) and I see ads, I simply add the URL from the ad itself to the hosts file - and blissfully continue reading the news sans ads on the side.

While I don't claim to block all the ads on the planet, this simple easy-to-maintain system works for me. And, I'm sure for many others (otherwise the main /etc/hosts file wouldn't be constantly maintained on the net).

So, in summary, it's not perfect - but it works. And, it's trivial to maintain.

Now, I'm still not making use of the suggested programs to constantly change 'my' IP address so I'll have to explore that separately.

Also, I've set the Google open DNS servers in my home broadband router as my DNS servers, but I don't know how that plays a role in blocking domains.

---

### Post by chickenPie4breakfast on 2012-02-14
I use OpenDNS and havent noticed any ads

---

### Post by unspawn on 2012-02-15
> **rocksockdoc said:**
> the statement (..) may discourage others.
One can only hope. If only one in a billion would experience the method to be way more efficient than any prior millennium kludge can ever hope to be I'm happy already. 

Simple but fundamental example: 'egrep "[[:blank:]](ad|ad[0-9])\.' the hosts file currently yields 385 results. Any host not in your list you would have to search for (as you update sporadically) and add manually. What do I have? Just one line:
```
ad*.
```
which blocks any such host name. 
Without any effort.
All of the time.


> **rocksockdoc said:**
> this simple easy-to-maintain system works for me. 
Well good for you. The fact you only address maintenance and conveniently disregard the rest of my post, plus the fact you dismissed using external filtering DNS servers right from the start, does make me wonder though if you actually *are* interested in a quality solution...


> **rocksockdoc said:**
> And, I'm sure for many others (otherwise the main /etc/hosts file wouldn't be constantly maintained on the net).
*shrug* (Continued) Existence of things on the 'net itself is no proof of sanity, usability or the author not being misguided ;-p

---

### Post by bodhi.zazen on 2012-02-15
> **unspawn said:**
> One can only hope. If only one in a billion would experience the method to be way more efficient than any prior millennium kludge can ever hope to be I'm happy already. 

Simple but fundamental example: 'egrep "[[:blank:]](ad|ad[0-9])\.' the hosts file currently yields 385 results. Any host not in your list you would have to search for (as you update sporadically) and add manually. What do I have? Just one line:
```
ad*.
```
which blocks any such host name. 
Without any effort.
All of the time.[/code]

Which is why I abonded a hosts file as well. There are several proxies that use this principle (Privoxy). The result is much easier to maintain, although there is a bit of a learning curve.

---

