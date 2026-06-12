---
title: "Best way to secure data?"
date: 2011-03-26
forum: The Cafe
---

### Post by BandD on 2011-03-26
My sister's house recently got broken into and her laptop was stolen.  She's not the most tech savvy person in the world. Her account (Windows 7) wasn't password protected, which made it all that much easier to gain access to extremely sensitive data (i.e. SSN, birthdate, bank accounts, etc.).  Needless to say her identity was stolen.  She figured it out  quickly by a fluke. The person/people who stole her laptop tried to open a paypal account in her name, but the address they used didn't match the one on file at the major credit bureaus, so paypal sent her a letter to the address that was on file. 

All this got me thinking about how secure my data is. I have quadruple redundancy of my data (my main machine, an external HD, and on a NAS RAID 1 at my in-laws' house that I connect to remotely through ssh).  

What is the best way to protect my data across all of these devices?  Is encryption the only option?  What to you do?

---

### Post by ssam on 2011-03-26
after physical security (laptop locks might help) disk encryption is the only way to stop someone getting the data off the disk. even if she had a password to stop the thief logging in, the disk could have been removed and connected to another computer.

---

### Post by uRock on 2011-03-26
Password protect everything with different passwords. Firefox offers a master password for its stored passwords.

If private info is to be stored on a system, then encrypt it.

---

### Post by CharlesA on 2011-03-26
The only way to be sure your data safe from theft is to encrypt it.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-26
Ccrypt everything with a randomised 64-character password.

Remember to make sure your random numbers are truly random, and not pseudo-random like the /dev/random and /dev/urandom. Radioactive decay is a good true random generator, try a service like [hotbits]("http://www.fourmilab.ch/hotbits/").

---

### Post by mmix on 2011-03-26
[http://www.truecrypt.org/](http://www.truecrypt.org/)

not the best, but anyway.

---

### Post by t0p on 2011-03-26
> **mmix said:**
> [http://www.truecrypt.org/](http://www.truecrypt.org/)

not the best, but anyway.

I like Truecrypt too.  It's easy to use, and it's pretty strong.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-26
> **t0p said:**
> I like Truecrypt too.  It's easy to use, and it's pretty strong.

Except it's not Free Software. Relying on non-Free software for encryption is about as secure as not using encryption at all.

---

### Post by Sporkman on 2011-03-26
Encryption. It's the pork of the future.

I second the above suggestion re ccrypt. I use that for my own encryption, plus my home directory on my laptop is encrypted via the standard Ubuntu built-in encryption set up on install.

---

### Post by stmiller on 2011-03-26
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Except it's not Free Software. Relying on non-Free software for encryption is about as secure as not using encryption at all.


It's free and open source. You can inspect every bit of the source code.

[http://www.truecrypt.org/faq](http://www.truecrypt.org/faq)

> Will TrueCrypt be open-source and free forever?

Yes, it will. We will never create a commercial version of TrueCrypt, as we believe in open-source and free security software.

It may not meet Debian's extreme standards of the meaning of 'free', but the source is available. 

:)

---

### Post by debiansu on 2011-03-26
Create a new symbolic language that only YOU understand. Next, write all your personal data down, pen on paper, in your language, and lock it in a safe. :P

---

### Post by Linye on 2011-03-26
Reading this topic made me feel weird that I don't have personal info in the laptop.

---

### Post by NovaAesa on 2011-03-26
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Remember to make sure your random numbers are truly random, and not pseudo-random like the /dev/random and /dev/urandom.
/dev/random/ provides very high quality, maximum entropy random data. We're not talking about pseudorandom number generation here, this is the real deal. /dev/urandom/ on the other hand is of lower quality; if you try to take too much random data at once and the entropy pool runs dry.

Your point still stands though, you definitely want to make sure you random data is of high quality.

---

### Post by handy on 2011-03-26
I don't keep my bank or credit card details on my computer.

If any other info' was stolen then it would just be an inconvenience whilst I changed passwords for whatever.

If someone wants your notebook, they'll just cut your security cable one way or another in a matter of seconds.

---

### Post by HermanAB on 2011-03-27
Hmm, *always* encrypt laptops.  They get stolen very frequently. I had one stolen too.

Fortunately, what usually happens is that the laptop gets re-imaged with Windows XP and sold on Ebay, so the data is usually erased before it is sold off.

---

### Post by Sean Moran on 2011-03-27
Keep your secrets on an encrypted USB flash drive.  Then when you leave your machine at home and go out, you can take the precious data along in your pocket.

---

### Post by 3Miro on 2011-03-27
> **Linye said:**
> Reading this topic made me feel weird that I don't have personal info in the laptop.

Browser history, autofill where you have entered your Credit Card, personal documents like forms for DMV. A simple birthday greeting card can tell the tiefs a lot. Are you sure you don't have anything personal.

Someone mntioned using a USB stick, you can do that, but then the USB stick itelf can get stolen.

Ultimately, encryption is the only way, even if Windows or Linux is password protected, tiefs can use liveCD to get everything.

---

### Post by Sean Moran on 2011-03-27
> **3Miro said:**
> 
Someone mntioned using a USB stick, you can do that, but then the USB stick itelf can get stolen.

The trick is, take the USB stick with you when you leave the house; leave the computer.  In the wallet or maybe even around your neck on the strings that some of them come with.  It's encrypted, so if you got held up at gunpoint and lost your wallet, there's not much chance of sensitive details like c/c numbers getting known (apart from the visa cards you already had in the wallet), and if you keep a second copy (update once a month or whenever there's a need), hidden somewhere in the house, you can always retrieve the data from that one if you got mugged on your way home from the computer shop and lost your main USB drive.

Nothing's perfect, but leaving sensitive data on a laptop hard disk isn't the wisest, because the hardware itself is stealworthy, and even if everything's enctypted, you wouldn't want to lose data that keeps track of things like bank accounts and card numbers.  That's why I reckon it's best to keep a note of secret information on a flash drive, that you can unplug and take with you wherever you go, and the computer you leave at home doesn't have anything on its hard disk that bad people might take advantage of.

---

### Post by BandD on 2011-03-27
Thanks for the input!  I figured encryption was the way to go.  

Now the question is which encryption tool to use.  Several people have recommended ccrypt.  Has anyone tried gnupg?  How about truecrypt?  Are there more/less performance hits when using any of these?

---

### Post by aysiu on 2011-03-27
I've found TrueCrypt the easiest to use.

---

### Post by Lightstar on 2011-03-27
My netbook only has 4gb of space (ssd).
I only have my operating system on it with programs.   All my data is stored on a SD card which I keep in my wallet when I travel.

I believe the most secure way to store data is using external media (also encryption if you can).   Placing your CD/DVD/BD/USB/Memory Cards in a different room.

If you go to big banks and such, none of the data is stored on the computer itself, they have data servers in a locked room.  If you're using a desktop you could do the same.  Place the computer elsewhere, and just keep your keyboard/mouse and monitor in the main room.

---

### Post by debiansu on 2011-03-27
If you want true security, you need to setup an "LTSP" or "Linux Terminal Server Project" server in secure room or location. You will store all your data on that, and then boot your machines from it using gPXE or etherboot, as clients of the LTSP server.

---

### Post by ve4cib on 2011-03-27
> **BandD said:**
> Now the question is which encryption tool to use.  Several people have recommended ccrypt.  Has anyone tried gnupg?  How about truecrypt?  Are there more/less performance hits when using any of these?

GnuPG is essentially an open-source version of PGP.  Its primary purpose is encrypting/signing e-mails and the like, not filesystem encryption.

Never used ccrypt, so I can't say anything about it.

TrueCrypt is a pretty solid program.  Lots of encryption/hashing options for varying levels of speed/paranoia trade-offs, and it integrates well with Nautilus (if you're a Gnome user).  It's primarily a GUI application, which generally makes it more user-friendly than some of the alternatives.


Besides using programs like TrueCrypt to encrypt specific directories/files on your machine you should also look into true filesystem encryption.

There is an option when you install Ubuntu to encrypt your home directory.  Use this option.  Your /home/username directory is encrypted, and mounted when you log in.  It means anyone who steals your computer will actually need your password in order to mount the encrypted directory to see what's inside it.

Other things you can do are to mount /tmp as a tmpfs (i.e. allocate a chunk of RAM to be /tmp, so it gets wiped every time you reboot), and encrypt your swap file/partition.

[Here](https://help.ubuntu.com/community/EncryptedFilesystemHowto) is a link with some instructions on how to set up encrypted file systems under Ubuntu.  You might find some of them useful.

---

### Post by dgw on 2011-03-27
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Ccrypt everything with a randomised 64-character password.
Random 64-character passwords aren't realistic for the average user. Most people will not be able to memorize that, and will end up writing it on a sticky note on their monitor, or copy/pasting it from a plain text file. Using even a weak encryption password will protect you from data theft if a laptop is stolen (unless it's stolen by a government agency or by someone who is willing to spend months trying to bruteforce the password - not realistic if it's just a laptop thief who wants to sell it on ebay).

---

