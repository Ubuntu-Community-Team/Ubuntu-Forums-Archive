---
title: "Trying to configure KVM having issues with python"
date: 2020-05-06
forum: Virtualisation
---

### Post by bigpah793 on 2020-05-06
hi,

 I am a little new to linux I am running Unbuntu 20.04 and current ver of python.
here is where i am stuck following the git link at the bottom of my post. 


```
al@LinuxTop:~$ cd OSX-KVM
al@LinuxTop:~/OSX-KVM$ ./fetch-macOS.py
/usr/bin/env: &#8216;python&#8217;: No such file or directory

```

I keep getting the " /usr/bin/env: &#8216;python&#8217;: No such file or directory" error, I have searched the forum and tried to use python 2.7 as well to avail


[https://github.com/kholia/OSX-KVM](https://github.com/kholia/OSX-KVM)

any and all help is appreciated.

---

### Post by TheFu on 2020-05-06
"python" or python2 aren't part of the 20.04 it seems.   

```
$ which python3
python3             python3-futurize    
python3.8           python3-pasteurize
```

python2 and python don't find anything in the path.

My first attempt would be to install python2.7.
```
sudo apt install python2.7
```
Looks like that should get the base system installed.  Then you just need to modify the script to point at the python2.7 program.

---

