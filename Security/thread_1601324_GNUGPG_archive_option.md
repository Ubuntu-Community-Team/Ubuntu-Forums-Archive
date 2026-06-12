---
title: "GNUGPG archive option?"
date: 2010-10-20
forum: Security
---

### Post by bcdudley on 2010-10-20
Looking for a quick answer on gnugpg.
We have been using the full commercial version of PGP for several years. I am wanting to migrate up to OpenPGP using GNUGPG.

One of the options in PGP was --archive and --output. With that command, I could archive multiple files into a single file. My command would read something like:
> PGP --encrypt filename.pdf --recipient 0x12345678 --archive --output encryptedfile.pgpI am trying to find an option within GPG that will perform the same function. I know I could compress them all first, then just encrypt the compressed file, but I would much prefer to do it all with a single command if possible.

What I have gotten so far is:
> gpg --recipient [email]somebody@email.com[/email] --output test.pgp --encrypt-files *.pdfwhich outputs 
> gpg: --output doesn't work for this commandThank you.

---

### Post by rookcifer on 2010-10-20
I think the 

```
--encrypt-files files
```

does what you want.  So for instance:

```
gpg --encrypt-files secret.pdf secret2.pdf secret3.pdf --recipient 0x12345678 --output newfilename
```

You can also view the entire GPG manual by typing:

```
man gpg
```

---

### Post by anomie on 2010-10-20
As gpg(1) sees it --output and -r are options, and --encrypt is an operational command. 

So you need to change the position / order around a bit, a la: 
```
$ gpg --output foo.enc -r somerecipient --encrypt foo.clear
```

--

edit: Sorry, never mind. Totally misunderstood the question.

---

### Post by bcdudley on 2010-10-20
The --output does need to come before the --encrypt function, however it is telling me that it does not work for this command when I add the --encrypt. If I put --output after the --encrypt, it sees it as another file to encrypt and fails. 

I have been over the man pages for hours and hours trying to find an answer.

The --encrypt-files is the correct function to use, however, when I do that, it encrypts each file individually. For example, if I have secret1.pdf and secret2.pdf. I will wind up with secret1.pdf.gpg and secret2.pdf.gpg.

What I need to end up with is a single file containing both of the original files.

Thank you.

---

### Post by anomie on 2010-10-20
Gotcha - same behavior confirmed here BTW. 

```
$ gpg --version
gpg (GnuPG) 1.4.10
...

$ gpg --output baz.enc -r somerecipient --encrypt-files foo bar 
gpg: --output doesn't work for this command

```

I don't have an elegant solution without using a pipeline / a couple distinct commands (e.g. bundling up the files either pre- or post- encryption, which you said you don't want to do).

---

### Post by bcdudley on 2010-10-20
I just checked with our programmer and the company we are sending files to. I can send them as multiple files without an issue. Thanks for the help.

---

