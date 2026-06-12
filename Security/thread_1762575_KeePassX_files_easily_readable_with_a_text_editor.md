---
title: "KeePassX files easily readable with a text editor"
date: 2011-05-19
forum: Security
---

### Post by inearlygaveup on 2011-05-19
Hi,
I have noticed and this now worries me, if I export a KeePassX xml file then open it with a text editor I can see all my “private” details.

Just tested it on my old desktop with Slitaz and open the exported file with leafpad text editor and I can see my details just the same.

Previously I used RoboForm and when viewing an exported file in the same way you could not make out any of my details. 

**Is KeePassX designed this way** or have I not used KeePassX correctly.

I have posted this on KeePassX forum and emailed them direct with no response so far.

Ubuntu 11.04.

---

### Post by Soul-Sing on 2011-05-19
> **inearlygaveup said:**
> Hi,
I have noticed and this now worries me, if I export a KeePassX xml file then open it with a text editor I can see all my &#8220;private&#8221; details.

Just tested it on my old desktop with Slitaz and open the exported file with leafpad text editor and I can see my details just the same.

Previously I used RoboForm and when viewing an exported file in the same way you could not make out any of my details. 

**Is KeePassX designed this way** or have I not used KeePassX correctly.

I have posted this on KeePassX forum and emailed them direct with no response so far.

Ubuntu 11.04.

.kdb should be the format of a keepass file.

---

### Post by inearlygaveup on 2011-05-19
> **leoquant said:**
> .kdb should the format of a keepass file.
Hi,

The only _**export**_ option it gives me is txt or xml

---

### Post by Joe of loath on 2011-05-19
The export function will be unencrypted, so you can import it elsewhere. You should treat the exported file like a private encryption key, keep only one copy, and securely delete it every time you move it.

---

### Post by inearlygaveup on 2011-05-19
> **Joe of loath said:**
> The export function will be unencrypted, so you can import it elsewhere. You should treat the exported file like a private encryption key, keep only one copy, and securely delete it every time you move it.

Thanks nice to have it confirmed

What about those who use dropbox to sync KeePassx between PC’s.
Does this mean they are simply relying on dropbox's security or is there another way.

Must admit that if I store anything I am a bit concerned about I usually 7zip it with a password. So far I haven't let anything of real importance out of my sight.

---

### Post by Joe of loath on 2011-05-19
> **inearlygaveup said:**
> Thanks nice to have it confirmed

What about those who use dropbox to sync KeePassx between PC’s.
Does this mean they are simply relying on dropbox's security or is there another way.

Must admit that if I store anything I am a bit concerned about I usually 7zip it with a password. So far I haven't let anything of real importance out of my sight.

Maybe they have the encrypted file on dropbox, maybe they're hoping that their dropbox password is secure :lol:

7zip with a password won't even stop a script kiddie, it's ridiculously easy to crack. You'll want to encrypt anything that's important.

---

### Post by inearlygaveup on 2011-05-19
> **Joe of loath said:**
> 
7zip with a password won't even stop a script kiddie, it's ridiculously easy to crack. You'll want to encrypt anything that's important.

I use TrueCrypt on my PC but what would you suggest for use on dropbox/ubuntu one

---

### Post by Joe of loath on 2011-05-19
Well, both are encrypted anyway, so just make sure your passwords are strong for both dropbox and any computers which it's synced with.

EDIT: Just remembered that files stored in the drobox folder can be accessed when the PC is off. It's best to encrypt them as you would normally, then, I believe in Ubuntu you can right click files and encrypt them in nautilus.

---

### Post by rookcifer on 2011-05-19
I see no reason to export the file at all -- just upload the encrypted KeepassX database file to dropbox and then you can access it from any machine.  No one but you is going to be able to view it since the file is encrypted from the start.

In my case, I have my database file inside a folder that is synced with Ubuntu One.  I have Keepassx setup to look in that directory when looking to open the database file.  This way any changes I make or any passwords I add are automatically synced and stored securely once I close the database file.

---

### Post by inearlygaveup on 2011-05-19
Thanks to leoquant, Joe of loath & rookcifer you've given me plenty to go on, started to look for a file encryption tool – but then remembered that my Ubuntu installation is encrypted so I shouldn't need encrypt individual files/folders to should I.

---

### Post by bodhi.zazen on 2011-05-19
Just share the database *.kdb and do not export / import it.

If you export it , encrypt the exported file, with say gpg .

---

### Post by Telengard C64 on 2011-05-19
> **bodhi.zazen said:**
> Just share the database *.kdb and do not export / import it.

If you export it , encrypt the exported file, with say gpg .

^ The best solution.

Also available: [ccrypt](http://manpages.ubuntu.com/manpages/lucid/en/man1/ccrypt.1.html)

Frankly, I can't understand what OP is worried about. KeePassX encrypts its database quite securely. If you don't want a plain text file of your KeePassX data to exist, then don't create one.

---

### Post by donato roque on 2011-05-19
If you are using dropbox or ubuntuone to sync with your other machines, there's no need to use export function nor the xml format. Just save your database in .kdb format. Open the .kdb file with KeePassX on that other machine. If you are using Windows there's KeePass/Keepass2 for windows. That goes with Mac users too.

---

### Post by inearlygaveup on 2011-05-20
Agree with everyone above and thanks.

*A couple of other questions* 
1 - Where is the .kdb file normally kept in Ubuntu
2 – Which is safest Dropbox or Ubuntu one

---

### Post by Telengard C64 on 2011-05-20
> **inearlygaveup said:**
> Agree with everyone above and thanks.

*A couple of other questions* 
1 - Where is the .kdb file normally kept in Ubuntu

IIRC you can save it wherever you like when creating the database for first use. FWIW mine is at **~/.keepassx/keepassx.kdb**

---

### Post by bodhi.zazen on 2011-05-20
> **Telengard C64 said:**
> IIRC you can save it wherever you like when creating the database for first use. FWIW mine is at **~/.keepassx/keepassx.kdb**

I keep my .kdb on a flash drive and use both a key and a password to open it.

key is on my hard drive

So to open the database you need both a flash drive and key on a hard drive (and a password).

---

