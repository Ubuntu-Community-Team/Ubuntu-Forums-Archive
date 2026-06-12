---
title: "How to move public and private GPG keys to another machine using a USB drive"
date: 2012-06-06
forum: Security
---

### Post by yeehi on 2012-06-06
I have used Seahorse to create a GPG key for public key encryption. 
I want to use the same key on another machine.
How do I get the key - public and private, into a usb drive and then into seahorse on the other machine?

Thank you!

---

### Post by thnewguy on 2012-06-06
I don't know about Seahorse specifically, but you can copy GPG keys (public and private) between machines by copying the ~/.gnupg folder from your current account on the old machine to your account on the new machine.

---

### Post by yeehi on 2012-06-07
Thank you, thenewguy!

What is the path to /.gnupg? I did a search for it on thenk file system and nothing turned up.

I think that the . in /.gnupg means that it is a hidden file. Maybe I need to tweak my folder browser to show hidden files somehow...

---

### Post by spynappels on 2012-06-07
You can also export the secret key from the terminal, as long as it will be imported on another GPG machine.

```
gpg --export-private-key [key-ID] -ao keyname.asc
```

Useful links:
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
[http://www.gnupg.org/documentation/manpage.en.html](http://www.gnupg.org/documentation/manpage.en.html)

---

### Post by yeehi on 2012-06-07
I tried this:

```
gpg --export-private-key [12345] -ao mykeyname.asc
```

and this:

```
gpg --export-private-key 12345 -ao mykeyname.asc
```

Both times I received the following error message:

```
gpg: Invalid option "--export-private-key"
```

---

### Post by spynappels on 2012-06-07
Sorry, my mistake.

```
gpg --export-private-key**s** [key-ID] -ao keyname.asc
```

Have a look at the man page in the second link in my previous post. It details all the different options available.

---

### Post by thnewguy on 2012-06-07
Sorry, the path ~/.gnupg is in your home folder. The "~" at the beginning is a symbol which means your home folder. So if your username is "robert" then the folder with your keys is

/home/robert/.gnupg/

---

### Post by yeehi on 2012-06-07
I tried looking for the /.gpg folder, but it is hidden and I do not know how to reveal hidden files. I don't know how to switch from having icons depicting the path in the folder browser to having a text line where I can type something in. So I can't use the copying the contents of the .gpg folder method at the moment.

I tried the command line to export the .asc file, and I finally got that to work. I checked the file contents in a text editor and it looked good. I transferred it to another machine and succesfully imported it into Seahorse. 

Unfortuately, it arrived in the "Other Keys" section, instead of my private keys section. I can use it to encrypt a file and send it to the owner - myself! But I can't use it to decrypt a message, I believe. Also, I expected to see a photograph on the key, but there wasn't one there.

I think I must have exported the public key, even though I tried to export a private key using that command in the command line. 

Sorry to trouble you with this!

---

### Post by donsy on 2012-06-07
To export your complete key, public/private, from Seahorse do this:


[LIST=1]
[*]In Seahorse click the "My Personal Keys" tab;
[*]select the key you want to export and right-click and select properties;
[*]click the Details tab and click the button for "Export Complete Key"
[/LIST]

---

### Post by cariboo on 2012-06-07
> **yeehi said:**
> I tried looking for the /.gpg folder, but it is hidden and I do not know how to reveal hidden files. I don't know how to switch from having icons depicting the path in the folder browser to having a text line where I can type something in. So I can't use the copying the contents of the .gpg folder method at the moment.

I tried the command line to export the .asc file, and I finally got that to work. I checked the file contents in a text editor and it looked good. I transferred it to another machine and succesfully imported it into Seahorse. 

Unfortuately, it arrived in the "Other Keys" section, instead of my private keys section. I can use it to encrypt a file and send it to the owner - myself! But I can't use it to decrypt a message, I believe. Also, I expected to see a photograph on the key, but there wasn't one there.

I think I must have exported the public key, even though I tried to export a private key using that command in the command line. 

Sorry to trouble you with this!

You can press Ctrl-h in nautilus to show hidden files graphically, or:

```
ls -la
```

In a terminal.

---

### Post by oldos2er on 2012-06-07
> **yeehi said:**
>  I don't know how to switch from having icons depicting the path in the folder browser to having a text line where I can type something in. 

Open a terminal, and a Nautilus (file manager) window. Use the file manager to find the required folder, drag and drop it into the terminal; the patch will be automatically entered in the terminal.

---

### Post by thnewguy on 2012-06-08
> **oldos2er said:**
> Open a terminal, and a Nautilus (file manager) window. Use the file manager to find the required folder, drag and drop it into the terminal; the patch will be automatically entered in the terminal.

I think the previous poster meant they wanted to be able to type in an address into their file browser, rather than clicking on visible icons. Assuming you are using the Nautilus file browser, then a location can be typed in by either going to the "Go" menu and clicking "Location..." or by pressing CTRL+L

Also, if you're looking for hidden files, go to the View menu and select "Show Hidden Files" or press CTRL+H.

---

