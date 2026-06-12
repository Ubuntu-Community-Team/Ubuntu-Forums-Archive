---
title: "ls bash error"
date: 2012-04-06
forum: Server Platforms
---

### Post by Fertech on 2012-04-06
I don't remember what I type at the terminal I only remember that at the end I put ls, so after that I got an error, so then  I copy the ls bash file from another ubuntu and put it on a usb drive and then copy the file to my other ubuntu, but now I get this error>>> 

```
:~$ ls
bash: /bin/ls: cannot execute binary file
```

need some help to solved this problem.

---

### Post by codemaniac on 2012-04-07
Why did you do that ? Binaries of one installation may not be compatible to other installation .
Once I had accidentally deleted a very important binary file on a HP-UX box then tried to get it from a similar installation .But that did not work .I had to retrieve it from an older tar backup of one of bins .

still you can execute permissions to ls and give it a try .
```
chmod a+x /bin/ls
```

---

### Post by Fertech on 2012-04-07
same error

---

### Post by whiskers751 on 2012-04-07
sudo apt-get install --reinstall coreutils

worked when I deleted the rm command

---

### Post by Habitual on 2012-04-07
terminal >
```
type -t ls
```

output please.

---

### Post by Fertech on 2012-04-07
I try 

```
sudo apt-get install --reinstall coreutils
```

Problem solved thanks I also try -t ls and got back in return "alias"

thanks for the information.

---

