---
title: "Turning old laptop into a E Book reader"
date: 2010-02-21
forum: The Cafe
---

### Post by I-75 on 2010-02-21
I have some old laptops,with  300 Mhz, 4 GB Hard drive with a maximum RAM of 64 MB. While I might be able to run puppy or Win 98 on them. 

Is there any Linux distro (or other kind of distro) that can run on such a low ram and be useful as a PDF reader? 

(While it might be possible to read some older PDF's in Win 98, Adobe requires 2000 or XP or higher for most of the newest PDF's)

 I would not care about not getting on the internet or doing modern apps on these. I would be primarily using these to read PDF's, and if the laptops got lost or stolen...it would be no big loss. Right now they are just taking up space and would like to put them to use.

If this is the wrong forum, please direct me to another thread (or another forum) where I could find such information. I did some searches and didn't see anything specific to my question. 

Thank You in advance for your replies.

---

### Post by dragos240 on 2010-02-21
> **I-75 said:**
> I have some old laptops,with  300 Mhz, 4 GB Hard drive with a maximum RAM of 64 MB. While I might be able to run puppy or Win 98 on them. 

Is there any Linux distro (or other kind of distro) that can run on such a low ram and be useful as a PDF reader? 

(While it might be possible to read some older PDF's in Win 98, Adobe requires 2000 or XP or higher for most of the newest PDF's)

 I would not care about not getting on the internet or doing modern apps on these. I would be primarily using these to read PDF's, and if the laptops got lost or stolen...it would be no big loss. Right now they are just taking up space and would like to put them to use.

If this is the wrong forum, please direct me to another thread (or another forum) where I could find such information. I did some searches and didn't see anything specific to my question. 

Thank You in advance for your replies.

Try LFS. All it needs to have is an xorg server, and an ebook reader. LFS would be the lightest you can do.

---

### Post by konqueror7 on 2010-02-21
pretty much every minimal install of linux distros would suffice...as dragos noted, you need X fore mostly, and an ebook reader,,,other things could be perhaps media manager or a lightweight browser, as it could also be of help...

---

### Post by qalimas on 2010-02-21
Go with a WM on top of X, such as OpenBox (forget GNOME or KDE).

Go with Swiftfox to get online if you need to, and Thunar for a file manager.

It'll be plenty to read PDFs.

---

### Post by The Toxic Mite on 2010-02-21
> **dragos240 said:**
> Try LFS. All it needs to have is an xorg server, and an ebook reader. LFS would be the lightest you can do.

Do bear in mind that he might not be l33t enough to do that.. lol

---

### Post by The Real Dave on 2010-02-21
An Ubuntu Minimal install, using command line apps such as MC for file management and eLinks for browsing the web. Then use that neat script that allows you to run a single app in Xorg, no WM, DE or anything. That's what I'd do at least. Would be snappy, and you'd have RAM to spare. Take a look at [KMandla's blog]("http://kmandla.wordpress.com"), he deals with stuff of that age, his main machine is a 120Mhz Pentium. So you might find some useful stuff there.

---

### Post by I-75 on 2010-02-22
Thank you for the great advice.

---

### Post by tgalati4 on 2010-02-22
slitaz, dsl, tinycore

---

### Post by Tristam Green on 2010-02-22
I thought there was supposed to be some open-source ebook software that'd be compatible with the Kindle Store and the nook store soon, with clients for Win7, OSX, and Linux?  Am I wrong?  I'd think that when coupled with a lightweight distro that's been stripped down, it'd work well.

---

### Post by Nerd King on 2010-02-22
> **Tristam Green said:**
> I thought there was supposed to be some open-source ebook software that'd be compatible with the Kindle Store and the nook store soon, with clients for Win7, OSX, and Linux?  Am I wrong?  I'd think that when coupled with a lightweight distro that's been stripped down, it'd work well.
Not sure if it's compatible with all of those but Calibre's got a lot of bases covered. Of course personally I'd go with using clit to convert any lit books to pdf and some suitable doc-pdf conversion tool to handle .doc files. Once that's done ebooks are a piece of cake to open (it's easier if they're all in the same format, then a single pdf app will do the job, saving space, and the conversion can be done on another more powerful computer if need be, or done on the reader as it's a batch job so speed's not so important).

---

### Post by dragos240 on 2010-02-22
I was actually going to suggest gentoo for the job, but the init scripts take a while, even on a good computer. I think a good distro for the job would either be LFS (not technically a "distro") or debian. You can really go bare with debian, and it would be easier to set up than LFS.

---

### Post by Nerd King on 2010-02-22
Only thing is, in my experience, getting a tinyX server up and running with debian's a pain. Admittedly I don't have MUCH experience but I have some. Bear in mind X is your big performance killer at that level, so if we can shrink down to that, and use Busybox instead of Gnu utilities we can shrink things right down. That and a suitably pared-down kernel would leave you with a real lean machine. TinyCore fits the bill for most of that, though you may find it hard work to set up certain items of software.

---

