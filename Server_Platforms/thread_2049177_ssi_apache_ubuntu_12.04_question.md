---
title: "ssi apache ubuntu 12.04 question"
date: 2012-08-28
forum: Server Platforms
---

### Post by bolognese on 2012-08-28
Hi everybody,

Some time ago I decided to learn some Linux and Apache configuring, so I installed 12.04 LTS. I downloaded my whole private website from my commercial hosting provider and decided that I want to configure the whole site myself on my notebook.

Yesterday I installed apache, which succeeded: "it works". I was even able to view my webpages, but they are not complete. The includes are missing. On my paid website everything is ok. Actually ssi is working too, which I can conclude from the date and time stamp file as a test.

The files which I include on my commercial website are menu.inc and footer.inc files are in the root, so the include is something like include virtual /menu.inc.

I think I know what the problem is, because in Linux/Apache now all files are in /home/josvdb/httpdocs/. On the commercial host they are just in httpdocs, which is the lowest directory, actually my root..

What can I do?

Thanks for any help already

---

### Post by Doug S on 2012-08-28
I think there might be a few solutions to your issue.
First, cann't you just put the include files where the system expects to find them?
Look in the /var/log/apache2/error.log file to know where:```
[Tue Aug 28 10:35:34 2012] [error] [client 192.168.111.100] File does not exist: /var/www/footer.inc, referer: http://s15.smythies.com/~doug/test.html
[Tue Aug 28 10:35:34 2012] [error] [client 192.168.111.100] unable to include "/footer.inc" in parsed file /home/doug/public_html/ssi_test2.shtml, referer: http://s15.smythies.com/~doug/test.html
```And once I put footer.inc in the correct place (/var/www/footer.inc), there was no more error.
Or, you could just put all of your files starting from the document root. Or you could change your document root.
 
P.S. possibly for other readers: ssi = [Server Side Includes]("https://help.ubuntu.com/community/ServerSideIncludes")

---

### Post by bolognese on 2012-08-28
Hey Doug,

Thanks for your attention.

What you actually want to explain is, that I should use /var/www/ as my root directory. I used the link you mentioned too last night, but it seems a lack of how a webserver really responds. I also have a lot of sub dirs containing html files that I want to behave like shtml.
On the ssi config page, there is an advice to create your own "mysite", so thats what I did.

Thanks again

---

