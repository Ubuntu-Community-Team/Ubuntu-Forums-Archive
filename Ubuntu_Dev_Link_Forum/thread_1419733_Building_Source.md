---
title: "Building Source"
date: 2010-03-02
forum: Ubuntu Dev Link Forum
---

### Post by sutherland1 on 2010-03-02
Hi All,
I have recently built a custom LiveCD using Remastersys, and have subsequently been asked to provide source for all packages installed to stay within the GPL.

Can anyone advise if there is an easy way to do this? I have been asked for an ISO file preferably.

Thanks in advance

---

### Post by Barriehie on 2010-03-02
This thread may help, [http://ubuntuforums.org/archive/index.php/t-14756.html](http://ubuntuforums.org/archive/index.php/t-14756.html)

What I'ld do is this: (make a file containing a list of all installed packages)
```

dpkg --get-selections | gawk '{ print $1 }' > ./packages
```

Then open up your favorite editor, that can run a macro, and build the following lines for each line of ***package***.  (emacs... :) )

```

sudo apt-get build-deb ***package***
sudo apt-get source ***package***

```

There's probably a way to do this with a one liner but I've not finished my coffee. 8)

HTH

Edit: I have no idea where it's going to put the source files.

---

