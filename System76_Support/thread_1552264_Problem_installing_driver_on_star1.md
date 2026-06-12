---
title: "Problem installing driver on star1"
date: 2010-08-13
forum: System76 Support
---

### Post by methmath on 2010-08-13
Finally got around to upgrading to 10.04, followed the instructions for upgrading the OS, and then the instructions at [http://knowledge76.com/index.php/LucidUpgrade](http://knowledge76.com/index.php/LucidUpgrade) for upgrading the driver. All went well until the step where you go System>Admin>System76 Driver and click Install. It ran for roughly 24 hours before I killed it.

Ran 
sudo system76-driver

returned error:

Traceback (most recent call last):
  File "/usr/bin/system76-driver", line 50, in <module>
    main()
  File "/usr/bin/system76-driver", line 44, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.6/UserDict.py", line 22, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION'

Don't know what to make of that... ?

edit: ran to install again and it worked. go figure....

---

