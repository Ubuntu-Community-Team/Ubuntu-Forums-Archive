---
title: "Ubuntuzilla creates incorrect profile path"
date: 2009-11-07
forum: Ubuntuzilla
---

### Post by cereal_girl on 2009-11-07
I am using Ubuntuzilla to run 32-bit firefox on a 64bit AMD. I have upgraded to 9.04 and freshly installed firefox from the repository and all related directories, and reinstalled Ubuntuzilla. Ubuntuzilla is incorrectly resetting my plugin path to /usr/lib/mozilla/plugins/libflashplayer.so   
Obviously, it is pointing to a file, rather than the appropriate dir, and therefore doesn't work. T(This same behaviour was occuring in 8.04. Repo version is working fine when Ubuntuzilla version is removed) 
Any ideas why this might be happening and how to fix it? If you could at least advise me on how to manually reset the plugin path, I would be grateful. It's a bit of a pain really - the whole reason for running Ubuntuzilla in the first place was to take advantage of plugins that don't seem to work on my 64bit machine!
Thanks! Please just let me know if you need any more information!

---

### Post by nanotube on 2009-11-07
Hi

Well, this certainly shouldn't be happening... and libflashplayer is nowhere specified in ubuntuzilla code...

Could you post the complete output of your ubuntuzilla install session?
```
ubuntuzilla.py -a install -p firefox
```

and also after the install, the output of 
```
ls -al /opt/firefox
```

---

