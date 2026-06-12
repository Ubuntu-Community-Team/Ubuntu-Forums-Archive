---
title: "Zip files on ubuntu web server"
date: 2010-03-28
forum: Server Platforms
---

### Post by group256 on 2010-03-28
Hi,

I have an Ubuntu web Server at home with Apache installed on it. I use it to access my regular files Using Firefox or any other browser. Now one thing is needed specially when I want to download a **folder** from my web server, then I have to start downloading the files inside the folder one by one which is not really practical. So, first idea in my mind is, to zip the folder on fly on server and download it. I have seen some actual websites that they do it. Does anyone know how I could do it???

Thank you so much.

---

### Post by craigp84 on 2010-03-28
IIRC there's a firefox extension (called <something>get IIRC) that allows pretty straight forward recursive downloading of a directory served up via HTTP.

To do it server side you need some more smarts on the server than just apache. There might be an apache module which can do this? Never come across one myself though.

The way i'd do it, is just a perl or python script (depending on whether i just want to get it done, or i'm being paid to do it respectively :-). It's small beer to serve up directory listings (have a google) then serve up a chosen directory as a zip file.

Only concern would be CPU impact, probably irrelevant for a small (<100 users) site.

Hope this helps

---

### Post by R.Bucky on 2010-03-28
If this would only be used by yourself or trusted users, you could simply open up a GUI ssh session with Ubuntu Desktop or ftp with Winblows using Explorer.

---

### Post by group256 on 2010-03-28
Thank you so much,

Firstly, I wouldn't mind to write some codes using Perl and Python(Although I have not tried Python before, but I do know a little bit about perl), so if it's possible please guide me to some good tutorials in the related topics.

Secondly, I do know that I can use GUI based SSH or FTP but I was wondering how I could use it simply by my browser. It needs to mentioned here that this web server is private and it's just for my own use so I don't need to turn on my external hard drive each time to access my files(and as I have an old laptop that I didn't use it anymore and now it's my web server with 160GB space). Anyway, if there is still any way, hard or easy one to do it, I would be more than grateful to know about them.

I will try the Firefox extension and report back later.

Many many thanks.

---

### Post by HermanAB on 2010-03-29
wget?

---

### Post by Ryan Dwyer on 2010-03-29
In your server script, execute the application you want to use (eg. gzip, zip, tar) with whatever parameters are needed. Then set the mime type to something like application/gzip and send the compressed data.

---

### Post by craigp84 on 2010-03-29
Pseudo code, coz, well,.... :-P

Script 1 -- download.cgi:

use CGI; (or one of the lighterweight alternatives if you want)

parse POSTed directory name

sanity check it (e.g. make sure request is for a sensible subdir, say under /var/www/pub/<whatever>/ and not requesting /var/www/pub/../../../etc/passwd). Clean up the filename (e.g. make sure it's not called '/path/to/mydir/ ; rm -rf /'

Now spit out a header because this next bit could take a minute and we don't want the browser to think we've stopped responding.

print "Content-type: application/x-zip-compressed\n";
print "Content-disposition: filename=whatever.zip\n\n";

Log the request to an audit log for this script.

If you're also running a trace log then fire in timings or whatever you need.

zip recursively whatever it is. Use open() with a pipe and not system() or backticks, for speed as well as safety... no sharp edges.

Job's a good 'un.

Script 2 -- browse.cgi:

opendir whatever
read in the directory entries
spit them out in a pretty page, and if it's a dir spit out a "download zipped copy" link beside it.

Hope this helps

---

### Post by group256 on 2010-03-30
Thank you very much guys,

I tried to find the Firefox extension, couldn't find anything similar.

Somehow, I am going to try the "craigp84" method and also see if I can dig something out from "Ryan Dwyer" statement.

Will keep you update.

---

