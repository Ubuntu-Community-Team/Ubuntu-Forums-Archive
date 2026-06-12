---
title: "Metasploit installer problems"
date: 2010-06-02
forum: Security
---

### Post by Guy Sibley on 2010-06-02
I downloaded the Metasploit Linux installer which is a file type .run (I have never encountered one of these, but I was told it is essentially a .bin).  So i tried to run it as I would a .bin

guy@Cuttlefish:~$ cd ~/Downloads
guy@Cuttlefish:~/Downloads$ ./framework-3.4.0-linux-i686.run

which generates this output

bash: ./framework-3.4.0-linux-i686.run: Permission denied

so I tried using sudo and it said command not found, which I thought was strange as it tried to tell me that I didn't have permission earlier.  I then logged in as root and got back to permission denied.  Has anyone had experience with this, I would like to start learning about and playing with Metasploit, so any help would be appreciated.

---

### Post by xolot1 on 2010-06-02
Have made sure the binary is executable?


```
chmod +x framework-3.4.0-linux-i686.run
sudo ./framework-3.4.0-linux-i686.run
```


By default files are not executable, but just read/write.

---

### Post by Guy Sibley on 2010-06-02
oh jeez, thanks I totally forgot that step. I am going to try that, thanks.  As I said, I am pretty new to this.

---

### Post by Guy Sibley on 2010-06-02
Yeah, thanks again. That was it.

---

