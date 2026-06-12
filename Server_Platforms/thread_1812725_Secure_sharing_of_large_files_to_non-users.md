---
title: "Secure sharing of large files to non-users"
date: 2011-07-26
forum: Server Platforms
---

### Post by dsjstc on 2011-07-26
We have a frequent need to allow non-technical users to transfer large, semi-private documents to and from non-technical outsiders.  Ease-of-use trumps security, but I do need enough security to prevent casual discovery of files by anyone other than the recipient.

Something that generates expiring or single-use URLs would be ideal.

Ideally, I'd like to use my existing apache/https server.  Is there anything out there that meets this need?

---

### Post by JKyleOKC on 2011-07-26
I have a slightly similar situation in that I need to receive large database files (for repair) from non-technical customers, and return those files after repair. Security is essential since some of the databases contain medical records while others have detailed financials (such as the general ledger) of the customer's business.

My solution was to set up an FTP server using proftpd, with three subdirectories: one for public access, one for incoming, and one for private data. The public directory is read-only, and is the only one that allows its content to be listed (the other two are completely hidden from public view). The "incoming" one is write-only, while the "private" one is read-only. I allow anonymous access to all three; in fact it's the only way anyone else can access the server at all.

I then created a small executable program that does the uploading; it contains all the data needed to reach the "incoming" directory and perform the transfer, but has only three action buttons: Browse (to select a file to upload to me), Send (to do the actual transfer), and Exit. This program is available for downloading from my public directory.

When I have repaired a file, I copy it to the private directory, with a unique filename, and send the URL link via Email to my customer who can then simply click the link to download the file.

You could do something similar, using a script to detect new uploads, contact the uploader to ask for a destination, then copy the file over to the private directory, and send its link to the destination user. It would need to assure that each file's name was unique, to avoid users from overwriting files from other users, but that could be done fairly easily.

Hope this helps, or at least gives you some ideas. The ability of proftpd to limit which FTP commands are available makes it quite easy to maintain security despite the many faults of the FTP protocol in general.

---

### Post by scorp123 on 2011-07-27
> **dsjstc said:**
> We have a frequent need to allow non-technical users to transfer large, semi-private documents to and from non-technical outsiders.

We use Dropbox for this. It's dead easy to use. Users can share folders with each other (all you need to know is the other person's e-mail address) and from there on files get automatically synced between them. Files to outsiders can be shared by using the "Generate a public URL" function in Dropbox.

So, for "ease of use" I'd recommend Dropbox. It just works across all major OS platforms (Mac OS X, Linux, Windows, iPad, iPhone, Android ...):

[http://www.dropbox.com/](http://www.dropbox.com/)


Another option that might work for you is "Teamdrive" maybe? With Teamdrive you can also include your own web servers:

[http://www.teamdrive.com/](http://www.teamdrive.com/)

How to use your own servers:
[http://www.teamdrive.com/free_server_selection.html](http://www.teamdrive.com/free_server_selection.html)

---

### Post by HermanAB on 2011-07-27
Easy: Use any FTP server and FileZilla client on Windows.

---

### Post by scorp123 on 2011-08-11
> **dsjstc said:**
> We have a frequent need to allow non-technical users to transfer large, semi-private documents to and from non-technical outsiders. 

BUMP.

I just found this and it works across platforms:
[http://www.binfer.com](http://www.binfer.com)

---

