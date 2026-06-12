---
title: "problem installing wine 1.2 in ubuntu 10.10"
date: 2011-04-17
forum: Wine
---

### Post by abhishek39 on 2011-04-17
my software center is not working whenever i try to install a software it is saying 
An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

when i click details it shows
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

plz help

also i wanted to install wine
so i followed the following steps
To add the line yourself, open Terminal and enter this command:

sudo nano /etc/apt/sources.list

After you furnish your password, the nano editor will open sources.list. Enter this line at the end of the file:

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

Save the file (press Ctrl-O), then close, open Terminal again and run:

$ sudo apt-get update

This will update the package cache. Now you can install Wine with the command:

sudo apt-get install wine

after the last step a license agreement page was displayed 
there was no option the agree of decline so i closed it manually by clicking the cross button.
after that when i am trying that again i is saying
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

what to do? urgent plz help.

---

### Post by cwwilson721 on 2011-04-17
If you would have scrolled down the text, you wouldn't have 'closed it manually by clicking the cross button.' the window.

Try opening a terminal, and try
```
sudo apt-get update
```

And try to install again

---

### Post by abhishek39 on 2011-04-17
> **cwwilson721 said:**
> If you would have scrolled down the text, you wouldn't have 'closed it manually by clicking the cross button.' the window.

Try opening a terminal, and try
```
sudo apt-get update
```

And try to install again

i scrolled down the text up and down for for than 20 times but there was no button to accept and exit.
well i tried sudo apt-get update

it got updated to some sorts of updates
then this error stopped the process

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
plz help

---

### Post by abhishek39 on 2011-04-17
hey wait...
i again got the same agreement page, with no exit button what to do.
i cant wait it open, plz help urgently

i am attaching the screenshot here.
u'll see <ok> written there but it's jst written, i cant click on it.

---

### Post by dino99 on 2011-04-17
open synaptic (system admin synaptic) then install wine 1.3.17 instead of 1.2.2

to get the latest, add this ppa to synaptic repo tab:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by gyussz on 2011-04-17
> **abhishek39 said:**
> hey wait...
i again got the same agreement page, with no exit button what to do.
i cant wait it open, plz help urgently

i am attaching the screenshot here.
u'll see <ok> written there but it's jst written, i cant click on it.

Use the right arrow key on your keyboard. It's a terminal window, which basically doesn't allow mouse interaction.

---

### Post by cwwilson721 on 2011-04-17
Either rt arrow , or down arrow, until the "ok" is highlighted, then press 'enter'

---

### Post by abhishek39 on 2011-04-18
> **cwwilson721 said:**
> Either rt arrow , or down arrow, until the "ok" is highlighted, then press 'enter'

thanks this worked, i had never thought, that is was so easy.

thanks you,

but can i play patriots via wine.

---

