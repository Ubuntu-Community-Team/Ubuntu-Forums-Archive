---
title: "Need help managing multiple GPG keys."
date: 2008-04-05
forum: Security Discussions
---

### Post by greenstar on 2008-04-05
[FONT=Tahoma][SIZE=2][COLOR=Black]I have just created two GPG keys, to keep separate professional and personal projects. I was trying to sign the [[COLOR=Blue]Ubuntu Code of Conduct[/COLOR]]("https://launchpad.net/codeofconduct/1.0.1/") according to the [[COLOR=Blue]instructions[/COLOR]]("https://launchpad.net/codeofconduct/1.0.1/+sign"). I used the [[COLOR=Blue]GnuPrivacyGuardHowto[/COLOR]]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") in [[COLOR=Blue]Community Documentation[/COLOR]]("https://help.ubuntu.com/community/") as well as the [[COLOR=Blue]Advanced GnuPG Concepts - Advanced Key Generation[/COLOR]]("http://ubuntuforums.org/showthread.php?t=687173&highlight=gpg+with+multiple+keys") thread to augment the instructions on the aforementioned Howto.

The problem is that when I use the instructions for signing the code of conduct, I don't get a choice of keys. Instead, the one I created for professional use is always selected. I don't know how to use the terminal to effectively use gpg with multiple keys. I just noticed that I can right-click a file and select "sign" from the context menu, but it outputs a .sig file that I don't know what to do with and does not give me the option to change output format. I can't use it for the code of conduct signing because that requires an .asc file that can be opened with ??? some app (?text editor?) or another so that I can copy & paste its contents into the sig box on the code of conduct page.

I found a [[COLOR=Blue]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3751897&postcount=5") that referenced three gui front-end packages by name. They are: Seahorse, gpa & Kgpg. This post also mentions a bug in the gpa version in the Ubuntu repositories. So I guess for now, that leaves Seahorse & Kgpg. I'm going to try them out.

They both seem to be good, but IMHO, Kgpg is a bit simpler to use and appears to have a bit more functionality. Both are also in the universe repo. I can use either of these to manage multiple keys, but the problem of getting one of them to output a usable signature is still looming. [I]Can anyone tell me how to get a usable .asc signature file out of one of these apps?

[/I] Although after encountering the aforementioned problem, something I read in the [[COLOR=Blue]GPGHowto[/COLOR]]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto#head-07fb6c57086eca90167f7ba1bd2b1895b6386534") sunk in. I realized that I need to get my key signed before I sign the code of conduct so that my signature can be verified as valid.

That's going to be another problem, as there's no one on [[COLOR=Blue]BigLumber[/COLOR]]("https://biglumber.com/x/web?mp=1") or the [[COLOR=Blue]Debian list[/COLOR]]("https://nm.debian.org/gpg_offer.php") for GPG key signers in my city. In fact, there are only 2 people in my state, and none in the next nearest state. Maybe I should organize something in my area. Problem is, we'd still need someone in the strongly connected set in attendance.

Thanks for your time and assistance.

Greenstar
[/COLOR][/SIZE][/FONT]

---

### Post by kevdog on 2008-04-06
Eh Yea.

That thread: Advanced GnuPG Concepts - Advanced Key Generation
I should really get around to finishing that tutorial.  I think my motivation was a little bit battered when I so no responses to the tutorial.  So sorry about that.

I tried those links you provided.  I don't have a launchpad account, so they were not much help to me.

What are you trying to do?  Sign a file with one of your keys?  So obviously you want to sign the file with one of your signing keys.  

Im not sure about the key signing part unless this is required.  This just builds the web of trust.  However if you are signing a file and sending it to someone, the recipient usually has to have the public keypair on their keyring, so that when you sign the file your your private signature key, they can verify the signature with your public signature key.  Usually keysigning parties are when you distribute your keys personally to other users.  Some dont go to such an extreme, and rather publish their public key on a website, that you could then copy into your keyring.

Again be more specific what you want to do.

---

### Post by greenstar on 2008-04-07
kevdog

Thanks for your reply.

Here are the instructions that I can't get through:

>                    To sign the code of conduct:[LIST=1]
[*]                                            [Download]("https://launchpad.net/codeofconduct/1.0.1/+download")                       the file to your own computer and read it carefully                       to ensure you agree to it.
[*]                                            If you want to, add extra spaces or blank lines between words                       in the file.                       (This helps protect against other people trying to                       forge your signature.)
[*]                                            In a terminal, run the command:[INDENT]                       gpg --clearsign UbuntuCodeOfConduct-1.0.1.txt                       [/INDENT](or whatever filename you gave to the code).                       This will create a file with a name like                       UbuntuCodeOfConduct-1.0.1.txt.asc.
[*]                                            Open that new file,                       and copy and paste its contents into this box.                       Then click “Continue”.[/LIST]Signed Code                (Required)Step 3 is where I'm hung up. The command given doesn't provide for specifying a key when more than one are present. It just defaults to one, and not the one I want at present. I just need to sign the code of conduct with the desired key and get it to output the file as a *.txt.asc (I think that's an ascii armored text file.) so I can copy and paste the contents into the form in launchpad.

I installed kgpg & seahorse to facilitate a learning curve for myself, but I'm not allergic to the terminal. 

ChaChing!\\:D/

I just figured out how to do it via terminal. I found a file named gpg.conf in ~/.gnupg and thought I might investigate further. when I opened the file I found this:

(not my actual key id)
```
default-key  XXXXXX01
```so I added:
```
default-key  XXXXXX02
```and commented out the first entry, so now I have this:
```
# default-key  XXXXXX01

default-key  XXXXXX02

```Easy enough until I come up with something better. It would be great if I didn't have to edit the conf file each time I need to use a different key from the last time. 

So I guess my question has become:

[B] Is there an easier way to switch between keys when signing files than editing ~/.gnupg/gpg.conf each time to change the default key?
[/B] 
Thanks for your time & help.

Greenstar

---

### Post by kevdog on 2008-04-07
Try this -- I think you use the -u flag or the --user flag.  So something like

gpg -u XXXXXX02 --clearsign UbuntuCodeOfConduct-1.0.1.txt

or 

gpg --user XXXXXX02 --clearsign UbuntuCodeOfConduct-1.0.1.txt

---

### Post by greenstar on 2008-04-07
> **kevdog said:**
> Try this -- I think you use the -u flag or the --user flag.  So something like

gpg -u XXXXXX02 --clearsign UbuntuCodeOfConduct-1.0.1.txt

or 

gpg --user XXXXXX02 --clearsign UbuntuCodeOfConduct-1.0.1.txt

Thanks again, that's *exactly* what I was after. Outstanding.

Greenstar

---

