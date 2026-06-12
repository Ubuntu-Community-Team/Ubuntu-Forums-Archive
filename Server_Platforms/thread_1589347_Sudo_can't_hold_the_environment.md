---
title: "Sudo can't hold the environment"
date: 2010-10-06
forum: Server Platforms
---

### Post by emo1912 on 2010-10-06
I'm with  Linux  2.6.32-25-server #44-Ubuntu SMP Fri Sep 17 21:13:39 UTC 2010 x86_64 GNU/Linux , Ubuntu 10.04 Server
And I wanna execute the next script in bash profile ```

[[ -s "/usr/local/lib/rvm" ]] && . "/usr/local/lib/rvm"  # This loads RVM into a shell session.

``` to set up RVM environment . In regular users, when type this in .profile . Works prefect, if I do ```
sudo -s
``` this script not working . I tried to type this code in /root/.profile , /root/.bashrc ,  /root/.bash_profile , /etc/profile without result :( . Only way that work is when I paste the code directly in console after I'm already with root permissions with ```
sudo -s
``` . I think /root/.profile , /root/.bashrc ,  /root/.bash_profile , /etc/profile aren't execute when I do ```
sudo -s
``` .

I accept any advice and help. Thanks .

---

### Post by emo1912 on 2010-10-07
I soved the issue, just added next code in /root/.bashrc ```

if [[ -n "$PS1" ]]; then
  # .... everything that was in /root/.bashrc ....
fi
[[ -s "/usr/local/lib/rvm" ]] && . "/usr/local/lib/rvm"  
 

```
and used  ```
 sudo su
``` instead ```
sudo -s
``` 

P.S.
For these who don't know what is RVM [http://rvm.beginrescueend.com](http://rvm.beginrescueend.com)

---

