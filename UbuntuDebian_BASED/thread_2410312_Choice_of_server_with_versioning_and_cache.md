---
title: "Choice of server with versioning and cache"
date: 2019-01-14
forum: Ubuntu/Debian BASED
---

### Post by cogitans on 2019-01-14
I’ve been doing some research to accomplish my goal but I’m still not  completely sure of the conclusion. I hope this forum is the right place  to complete the quest &#61514;
  
The scenario is as follows: I want to improve the setup of a LAN with  multiple clients that communicate with a shared server on the internet.  The clients share a widespread branch of filetypes and filesizes. Some  files maybe a few GBs in size. Instead of every client communication with the server on the internet My  idea is to place a proxy-server where the LAN and the web is connected.  Now, this is where my discoveries goes into several directions. I think it might be a swell thing if the proxy-server had some sort of  backup of each file. Lets say each file would have a backup 2 or 3  versions prior to it’s present state. This would be achieved by using  SubVersion (the clients are mainly Windows 10 but other OS’s would  access it, too [like Mac and Ubuntu]. The proxy-server is Ubuntu,  though). The proxy-server would host some shared files; this might be the files  of GBs in size. Apart from this the server should host several files  according to the demands of each client-requests, too. This would be  individual docx-files, pdf-files and other types. In the process of finding a solution I found that either Apache  (Traffic?), Nginx (Caching) or Squid would be possible solutions. But  I’m not sure if SubVersion is the best solution. And if SubVersion is  compatible along with each choice of server. On top of that I just  discovered that not every server provides full features of caching (page  5 at [http://static.usenix.org/events/lisa11/tech/slides/hedstrom.pdf](http://static.usenix.org/events/lisa11/tech/slides/hedstrom.pdf)). And it looks like I can’t setup a single server to provide all the desired features according to this picture: [https://en.wikipedia.org/wiki/File:LAMP_software_bundle.svg](https://en.wikipedia.org/wiki/File:LAMP_software_bundle.svg)  (1 server can’t provide both caching/proxy and versioning). I found some guides online to setup parts of the desired solution but  none of all the desires features in a complete setup. And I’m not even  sure if it’s possible or if I’m on the right track in my investigation.

  
Any help would be deeply appreciated along with some step-by-step guides; preferably with images.

  
Thanks in advance.

  
Best regards.

---

### Post by TheFu on 2019-01-14
Interesting need.  I've never seen or heard of anything like this.  I think the problem is that multiple different sorts of vastly different files are included.
* code management
* huge media files
* light document management files
* local caching ... that breaks all these solutions.

For document management, check out Alfresco.  Each file would be checked in and checked out for changes. You can configure no version control of 5 or 20 or 200 versions to be retained.  I think you can setup automatic checkout/checkin.  Non-technical people in my group had trouble understanding this and continued to add dates to file names for versioning. They never trusted the DMS built-in, automatic, versioning.  In a DMS, it basically keeps complete copies of every version without any attempt at optimization.

Code control like SVN, CVS, or git are all designed to track differences in file versions.  This works great for text files, but fails quickly for documents, images, and media files.  The differences balloon in size making them worse than just using a DMS with 20 copies for the versioning.

Multi-GB files cause all sorts of problems.  They are slow to move around even on the LAN, and retaining multiple versions will eat up TB and PB of storage quickly.

Many industries have specific solutions.  Had a client that was an architecture firm with 100+ architects. They were constantly making different versions of buildings. They had a Windows Server solution just for managing their CAD diagrams, but all the pretty artwork and photos of before, during, and after constuction were stored in normal shared folders using CIFS manually organized by yyyy/mm-project/version/.  One of the engineers there had written a script to index all those files with metadata so everyone could quickly search for the "tall, skinny, tree" images quickly.

As for having a local cache, perhaps using something like nextcloud or seafile with read-only access to the DMS would fit that need?  I use nextcloud here to access NFS storage on other systems in a read-only manner.  Nextcloud cannot harm any of those files.

I have no clue about Windows access anymore.  Barely touch Windows computers anymore and haven't touched a Mac since 2011.

If this is for a home project only, then I'd just write a script to find the files I want, put them into an rsync "include-files" list and use rsync to make a local cache.  Creating a list of files by name, date, size, and owner isn't hard.

Anyways, hopefully those ideas will be helpful as you search for solutions.

---

### Post by cogitans on 2019-01-16
> **TheFu said:**
> Interesting need.  I've never seen or heard of anything like this.  I think the problem is that multiple different sorts of vastly different files are included.
* code management
* huge media files
* light document management files
* local caching ... that breaks all these solutions.


Thanks for the reply :-)

The files of GBs are ISOs. And it's just a couple of these files and they wont chance.

I don't know of Alfresco; I'll do some reseach about that :-)

The codecontrol isn't of the differences in the code itself but more about the entire document.

I didn't know that a cloud would serve as a local cache. I'll look into that, too.

---

