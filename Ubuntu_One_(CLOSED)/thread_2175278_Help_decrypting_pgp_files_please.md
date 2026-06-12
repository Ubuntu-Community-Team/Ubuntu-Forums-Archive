---
title: "Help decrypting pgp files please"
date: 2013-09-18
forum: Ubuntu One (CLOSED)
---

### Post by sgb77 on 2013-09-18
I have moved to linux mint, I am able to sync my files using the ubuntuone app. I get a bunch of pgp files in my directory, exactly what I see on the ubuntu one site.

My question is how do I restore all these pgp files to a folder somewhere in my system?
I have tried the following, but this just gives me a list of files in that particular .pgp file.

```
gpg -d file.gpg
```


The following will create a zip file with all the files and folders, but the files are no good.

```
gpg --output /home/user/test.zip --decrypt duplicity-full.20130307T014620Z.vol100.difftar*
```

If anybody can tell me what I'm doing wrong or if I need to use some other tool to do this, it will be greatly appreciated.

Thank you..):P

---

### Post by Dennis N on 2013-09-18
I can offer a few thoughts:

**gpg -d file.gpg** will decrypt with output sent to the terminal. If you can read it, file must have been a text file, and you are looking at its decrypted contents.

If it were not a text file, you would see decrypted but still unreadable output (for example, if it were an encrypted image, or an encrypted compressed archive).

**gpg -o filename -d filename.gpg** will decrypt **filename.gpg** back to the original, **filename**. I leave the extension when encrypting so that I know what kind of file I am dealing with. For example,

**gpg -c  statesecrets.tar.gz**

will encrypt to **statesecrets.tar.gz.gpg** by default

Later, when decrypting, you would know it is an encrypted .tar.gz archive, and can name the output file accordingly.

In your second box, was the encrypted file (duplicity.full..) originally a .zip file? Otherwise, this does not make sense to send output to text.zip.

That's really all the comment I can offer.

---

### Post by sgb77 on 2013-09-18
ok, I think I understand this whole encrypt/decrypt thing a little better.

When I run this command:
gpg --decrypt-files duplicity-full*.gpg

I get asked for the passphrase and get a duplicity-full*.difftar file.
I untar this file using the tar utility and get what looks to be my data, I got all exited to see some of my folders an files, however I navigate trhough the folder tree to get to a bunch of folders that have names of pictures, like img234.jpg which should be a picture, but it is now a folder with files inside it named only with numbers, 1, 2, 3..etc
When I try to open these files with an image editor it is no use, I try opening with a text editor, to find garbled text.

So, here is what I think, or at least drawing a conclusion from googleing, but I'm not sure. Since my computer crashed and I no longer have the keys I encrypted these files with, is what the problem is.
If someone can confirm or give other suggestions I'll really appreciate it.

Thanks!

---

