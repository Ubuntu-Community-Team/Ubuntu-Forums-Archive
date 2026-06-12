---
title: "What is the correct way to remove Ubuntu Studio?"
date: 2010-02-16
forum: Ubuntu Studio
---

### Post by dannyboytward on 2010-02-16
I'd really like to try out Ubuntu Studio, but I want to make sure I know how to remove it  before I do (I must have installed and uninstalled Ubuntu with Wubi 10 times before I finally commited to it).

While combing the the forums, I've found many different suggestions:

sudo apt-get purge ubuntustudio-desktop
[http://www.uluga.ubuntuforums.org/showthread.php?t=1388286](http://www.uluga.ubuntuforums.org/showthread.php?t=1388286)

sudo apt-get install ubuntu-desktop
[http://ubuntuforums.org/showthread.php?t=484651](http://ubuntuforums.org/showthread.php?t=484651)

sudo apt-get install ubuntu
[http://ubuntuforums.org/showthread.php?t=560060](http://ubuntuforums.org/showthread.php?t=560060)

sudo apt-get remove --purge ubuntustudio-desktop
[http://ubuntuforums.org/showthread.php?t=871610](http://ubuntuforums.org/showthread.php?t=871610)

Can anybody explain what the differences are between these?  And which method is the safest / most appropriate?

Thanks,
-dannyboytward

---

### Post by VertexPusher on 2010-02-16
```
sudo apt-get install ubuntu-desktop
sudo apt-get purge ubuntustudio-desktop
sudo apt-get --purge autoremove
```

---

### Post by dannyboytward on 2010-02-16
Thanks for the response.  I guess the answer is "e) all of the above" :)

Could you explain what these commands do specifically?  What would be left out if had used only one of them from another post?  Does the order matter? (I know that ubuntu-desktop and ubuntustudio-desktop contain some packages that replace each other, so does that mean it is necessary to install ubuntu-desktop before I purge ubuntustudio-desktop?)

And finally, why is there so much inconsistency on the forums?  If these commands are the final word, it would be nice to put this on the ubuntu studio support website ([https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)).

That's a mouthful of questions.  Hopefully someone can help me sort this out.

Thanks so much,
dannyboytward

---

### Post by VertexPusher on 2010-02-17
> **dannyboytward said:**
> Could you explain what these commands do specifically?
The first two commands basically tell the package manager to mark any Ubuntu Studio software package as "no longer required" unless it is part of the standard Ubuntu desktop as well. The third command removes all packages which are no longer required.

> What would be left out if had used only one of them from another post?
Removing the ubuntustudio-desktop package alone would not do much because ubuntustudio-desktop is just a "metapackage". It depends on a lot of other packages but does not contain any software itself. Removing a metapackage does not remove those other packages. They will remain installed until you issue the autoremove command.

> Does the order matter?
Yes, it does. If you uninstall both ubuntu-desktop and ubuntustudio-desktop, the autoremove command will consider a lot more packages as no longer required. The first command ensures that all the standard packages survive the autoremove step. Any package that you installed manually will survive the autoremove as well.

---

### Post by dannyboytward on 2010-02-17
Thanks again for the explanation.  I've added this to the Ubuntu Studio wiki FAQ here

[https://help.ubuntu.com/community/UbuntuStudio/FAQ](https://help.ubuntu.com/community/UbuntuStudio/FAQ)

Have a look and feel free to change it if I've missed anything.

---

