---
title: "Unlock SSH Private Key"
date: 2012-06-21
forum: Security
---

### Post by irishetalon007 on 2012-06-21
How do I "import" a private key into an ubuntu install so that I can access my SSH server? It's already in my ~/.ssh folder. this same private key was used to make the public key now on the server. To test functionality, I went into Applications/Preferences/Passwords and Keys and deleted the key so that it would prompt me for the key's passphrase again, but now I can't get it to do that. Trying to log in to the ssh server gives:

Permission denied (publickey).

When I try to use File/Import from the menu in "Passwords and Encryption Keys," i'm able to open the private key and successfully enter the passphrase. Details of the key are then shown.
Then I click "Import" in the bottom right, a dialog comes up that says:

Import Settings
Label:

and whether I leave Label blank or enter random stuff, In the end I get a red box that says "Import failed: no user has logged in"

plz help!

---

### Post by Lars Noodén on 2012-06-21
The public key should be copied to the file [font=Courier New]~/.ssh/authorized_keys[/font] over on the remote server.  The private key stays on the client and should not be copied anywhere.  If you cut-and-paste to [font=Courier New]authorized_keys[/font] be sure that the key is all on one line.  The permissions for [font=Courier New]~/.ssh/[/font] should be 700.

---

### Post by irishetalon007 on 2012-06-21
i believe those are all server-side settings, while my problem is with client-side.

Oddly enough, I got it working by doing the following, which I don't understand.

I went onto the server, copied the contents of authorized_keys into a file called mykey.pub, and copied this file into ~/.ssh on the client, so that the contents of ~/.ssh were:
mykey
mykey.pub.

Then when I try to log onto the server over ssh from the client, it asks me for the passphrase to my key again and it worked! I now see my key in gnome keyring.

Why in the world does the client require the public key to login?

---

### Post by irishetalon007 on 2012-06-21
I still dont' quite understand it, but I found if I rename my private key to id_dsa, I'm able to delete the public key. Only "downside" is I have to enter passphrase for key every time I logon to ssh server.

two questions:

is it unsafe to enter passphrase for id_dsa every time, as opposed to having it stored in Gnome Keyring?

also, is it unsafe to have the private key's name the default "id_dsa"?

Thanks!

---

### Post by CharlesA on 2012-06-21
You are able to delete the public key with no problems.

However if you rename the id_dsa file, you will have to specify the private key file in ssh -i /path/to/private/key user@host

---

