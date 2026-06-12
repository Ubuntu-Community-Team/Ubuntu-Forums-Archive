---
title: "Cross platform encryption for notes and passwords"
date: 2010-03-10
forum: Security
---

### Post by danielsbrewer on 2010-03-10
Hello,

I would like to be able to store all my important details and passwords in such a way that it is encrypted, easy to get the information out and is cross-platform.  Basically, I am thinking that if I kick the bucket that I would like to make it as easy as possible for others to be able to access this information using a pre-arranged password.

Ideally I would like the files to contain the program that is needed to extract the data i.e. importantinfoLinux.sh inportantinfoWin.exe (Just like a self-containing zip).  I haven't found anything along those lines.

The things I am currently thinking of is:
1) A password database program that is cross-platform like KeePass.  WIth the bundle contining the relevant installers for win, linux and OS X and the database file.
2) An AES encrypted zip of the data with relevant programs to open it e.g. 7-zip on windows, peazip on linux and OS X

Has anyone got any thoughts on this?  Any self-containing java encryption apps?

Thanks

---

### Post by partloer on 2010-03-17
Hi danielsbrewer,

I have used Truecrypt before and I think that it should work fine for what you need.  This is a cross-platform and open source encryption program.  You can use it to encrypt entire hard drive, thumb drive, or custom size.  

When the data is encrypted you can move everything just like a file when it is decrypted you can add folders/files as needed.  So adding either KeePass database of passwords or and Excel sheet of passwords both will work.  There is a variety of encryption algorithms such as AES-256, Serpent, Twofish, etc.

[http://www.truecrypt.org/]("http://www.truecrypt.org/")

Let me know what you think.

---

### Post by danielsbrewer on 2010-03-18
Thanks for that, and I like the look of truecrypt a lot but I don't think you could get a standalone bit of software that will be able to read the encrypted space without having it installed.  What I would like would be a USB stick with all the tools you need on it already.

Thanks for mentioning truecrypt though, it looks very useful for other stuff.

---

### Post by tubbygweilo on 2010-03-18
Look at it this way. If you can't get the authority to install and run truecrypt so as to decode your encrypted usb memory stick are you then  you can trust your data to that machine? ;)

---

