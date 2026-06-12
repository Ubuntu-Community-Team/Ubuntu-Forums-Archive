---
title: "Ubuntu One - From Scratch"
date: 2010-04-04
forum: Ubuntu One (CLOSED)
---

### Post by ubuMike on 2010-04-04
Hello,

I ran into trouble with my U1 client after upgrading to 9.10 in November.

I was getting the cloud with the '!' inside. I would click and Apport would send an error report.

This didn't help me much... So I decided to take matters into my own hands and 'sudo apt-get purge ubutuone*'

I then reinstalled U1 from the Ubuntu Software Center...

Now I get the same ! cloud. When I click it, It disappears!

How can I reinstall from scratch? What files do I delete?

---

### Post by duanedesign on 2010-04-05
ubuMike,
I am afraid that if you purge ubuntu One and reinstall you will still have the same issue. See [bug 498444]("https://bugs.launchpad.net/ubuntuone-client/+bug/498444")

That being said the following steps can be followed to completely remove the Ubuntu One client software, then reinstall, and test that the new install is working properly.

REMOVING UBUNTU ONE CLIENT
In order to completely remove the Ubuntu One client from your computer, please do the following (commands prefaced with $ are to be run in a terminal session, without the $ at the beginning):

1. Quit the Ubuntu One client
2. $ sudo rm -rf ~/.local/share/ubuntuone
3. $ rm -rf ~/.cache/ubuntuone
4. $ rm -rf ~/.config/ubuntuone
5. $ mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/
6. Open Applications->Accessories->Passwords and Encryption Keys, go to the Passwords tab, delete the Ubuntu One token
7. $ sudo apt-get purge ubuntuone-client* python-ubuntuone-storage*

----

REINSTALLING UBUNTU ONE CLIENT
And to reinstall the Ubuntu One client software, continue by following these steps:

8. $ sudo apt-get install ubuntuone-client* python-ubuntuone-storage*
9. Open Applications->Internet->Ubuntu One (or System->Preferences->Ubuntu One if you're on a newer version of Ubuntu One) and you should have to add your computer via the web page that comes up once you login to Ubuntu One

----

TESTING THE NEW UBUNTU ONE CLIENT INSTALL
And, finally, to ensure your account is working properly, do the following:

10. Put a small text file in the newly created ~/Ubuntu One/ directory and make sure that syncs correctly, if not, please report a bug by right-clicking on the Ubuntu One client and selecting "Report a Problem"
11. If all goes well this far, move the files and folders from ~/Ubuntu One_old/ to ~/Ubuntu One/ and the sync should happen

---

### Post by joshuahoover on 2010-04-08
> **aion4217 said:**
> what?

Is there something you're confused about that Duane provided in his reply above? I'd love to help clear up any confusion.

Thanks!

Joshua

---

