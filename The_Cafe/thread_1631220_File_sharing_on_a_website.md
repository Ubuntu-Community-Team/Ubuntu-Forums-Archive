---
title: "File sharing on a website"
date: 2010-11-26
forum: The Cafe
---

### Post by dpatel on 2010-11-26
Hi all -

Might be a simple thing but I want to have a file share area EITHER on a voluntary org website (not yet created) OR through a third party site which has the following features:

- Set permissions for viewing, editing, etc.
- Allow adding of tags (or brief description) to any file
- Search based on filename or tag
- Secure
- Free!

Nice to have: allow viewing/editing docs, spreadsheets without downloading.

Can you guys recommend an appropriate software for the website.

---

### Post by m4tic on 2010-11-26
I suggest staying away from file sharing activities, have you read the news on the pirate bay case? The thing is, what happens when many people start using your service and start sharing illegal material, i suggest you think about this and if you decide to go along with it make sure you have insurance.

---

### Post by Penguin=) on 2010-11-26
Use YouTube, you don't need to pay, you can upload anything at all (nothing racist or stuff)
and its really easy!





But if your looking for JUST a website then, i woulden't really do that.
Its quite dangerous.

---

### Post by Penguin=) on 2010-11-26
> **m4tic said:**
> I suggest staying away from file sharing activities, have you read the news on the pirate bay case? The thing is, what happens when many people start using your service and start sharing illegal material, i suggest you think about this and if you decide to go along with it make sure you have insurance.


I agree with you.

---

### Post by joepie91 on 2010-11-26
> **Penguin=) said:**
> Use YouTube, you don't need to pay, you can upload anything at all (nothing racist or stuff)
and its really easy!





But if your looking for JUST a website then, i woulden't really do that.
Its quite dangerous.

I may be wrong, but YouTube doesn't allow any uploads besides video files, right?

Also, watch out with filesharing. The biggest threat is not in illegal files (with enough moderation that can be easily avoided) but in the filesharing software itself. I know of no hosted solutions that are free, so you'll have to install a script on your own hosting... and filehosting scripts are very known to contain exploits. And a lot of them.

---

### Post by dpatel on 2010-11-26
Oops, when I meant file sharing I did not mean like DVDs or the like.

I am talking about sharing docs, spreadsheets, etc.

I've looked at Google docs, SkyDrive, etc but they don't fit all my criteria (such as tagging, etc).

Basically, I'm looking for something very simple that multiple users can use via their browser to access files. They must also be able to upload to the shared folder and tag it.

---

### Post by d3v1150m471c on 2010-11-26
[http://www.mediafire.com]("http://www.mediafire.com/")

that's what i use.

---

### Post by aeiah on 2010-11-26
what about dropbox? or just.. google docs?

or you could get yourself a web server and install something yourself. see if sf.net has anything useful and then see if you can get a free shell with web hosting from devio.us or something

---

### Post by czr114 on 2010-11-26
m4tic is right, but a lot of this depends on where you're located. Different countries have different safe harbor laws applying to sites which serve legal purposes but can be abused in illegal ways without the knowledge of the site's operator.

---

### Post by aeiah on 2010-11-26
christ people.. what makes you think OP is talking about *illegal* filesharing?

---

### Post by dpatel on 2010-11-26
> **aeiah said:**
> christ people.. what makes you think OP is talking about *illegal* filesharing?

I'm not. Thank you!

I do some volunteer work with a youth group and I want to be able to share files with other volunteers; and allow them to also share their files. And tag them so they are 'categorised'.

I can either do this on a personal website or use a 3rd party site (like dropbox). As yet I haven't found a 3rd party that meets all my criteria. So I posted here for suggestions of 3rd party sites OR simple software I can install on a website...

---

### Post by czr114 on 2010-11-26
> **aeiah said:**
> christ people.. what makes you think OP is talking about *illegal* filesharing?
The OP made it sound like he wanted to set up a Dropbox clone. Those aren't illegal filesharing, but they attract people who do.

---

### Post by SeijiSensei on 2010-11-26
Perhaps the easiest method is WebDAV using the [mod_dav module for Apache]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html").  It basically creates a shared folder tree to enable authorized users to share files.  No tagging or anything like that, though.  It's more like a Windows file share.

At the other end of the spectrum is [dspace]("http://www.dspace.org/").  This has it all, but it might be overkill for your needs.

A Google search for "php-based file sharing" brings up a number of other options that would run on Apache with PHP installed.

---

### Post by Oxwivi on 2010-11-26
> **dpatel said:**
> Basically, I'm looking for something very simple that multiple users can use via their browser to access files. They must also be able to upload to the shared folder and tag it.
Well, I don't know about tagging and all, but multiple people can easily view documents at Google Docs, and you can even get them to edit it in real time.

---

