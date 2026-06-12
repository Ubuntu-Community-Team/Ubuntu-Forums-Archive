---
title: "which package include php5 with with-freetype-dir option?"
date: 2008-02-21
forum: Server Platforms
---

### Post by u007 on 2008-02-21
hi,

anyone know which package contains php5 with-freetype-dir option?
I can't seems to find the package...

please help...

best regards,

James

---

### Post by rapiscan on 2008-02-25
Hello there.  I think it's likely that you will have to compile php5 from source if you're interested in specific options like this.  It seems like a daunting task at first, but really isn't too bad in the end. Just google for How-To's on how to install PHP5 from source and you should get some good walk throughs.  

You will need the build-essentials package to compile source code, which can get with:
```
sudo apt-get install build-essentials
```

You can then download the source code for php5. Make sure to read the README, which will provide general instructions for compiling.

Before compiling, you set the options during the configuration step, so this is a very important step.  Make sure that you have all of the configuration options correct before you actually compile.  Good luck.

---

