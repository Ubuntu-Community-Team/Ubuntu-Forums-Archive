---
title: "Downloading specific version of sudo 1.8.27"
date: 2022-05-29
forum: Ubuntu/Debian BASED
---

### Post by ramesh8 on 2022-05-29
I am trying to install older version SUDO But whenever i do sudo make install I get this error ,
```

if test -d ./.hg && cd .; then \
    if hg log --style=changelog -b default > ChangeLog.tmp; then \
        mv -f ChangeLog.tmp ChangeLog; \
    else \
        rm -f ChangeLog.tmp; \
    fi; \
elif test -d ./.git && cd .; then \
    ./log2cl.pl -b master > ChangeLog; \
else \
    echo "ChangeLog data not available" > ChangeLog; \
fi
for d in lib/util  plugins/group_file plugins/sudoers plugins/system_group src include doc examples; do \
    (cd $d && exec make pre-install) && continue; \
    exit $?; \
done
make[1]: Entering directory '/home/kali/Downloads/sudo-1.8.27/lib/util'
make[1]: Nothing to be done for 'pre-install'.
make[1]: Leaving directory '/home/kali/Downloads/sudo-1.8.27/lib/util'
make[1]: Entering directory '/home/kali/Downloads/sudo-1.8.27/plugins/group_file'
make[1]: Nothing to be done for 'pre-install'.
make[1]: Leaving directory '/home/kali/Downloads/sudo-1.8.27/plugins/group_file'
make[1]: Entering directory '/home/kali/Downloads/sudo-1.8.27/plugins/sudoers'
Checking existing sudoers file for syntax errors.
>>> /etc/sudoers: syntax error near line 51 <<<
parse error in /etc/sudoers near line 51
make[1]: *** [Makefile:384: pre-install] Error 1
make[1]: Leaving directory '/home/kali/Downloads/sudo-1.8.27/plugins/sudoers'
make: *** [Makefile:103: pre-install] Error 2

```
I need to overwrite the current version of sudo 1.9.10.
Thank You

---

### Post by ActionParsnip on 2022-05-29
What is the output of
```

lsb_release -a; uname -a

```

---

### Post by ActionParsnip on 2022-05-29
Sounds like you are using Kali (Not Ubuntu) and have messed with sudoers and botched the file

---

### Post by ramesh8 on 2022-05-29
Yes i am using kali . 
No LSB modules are available.Distributor ID: Kali
Description:    Kali GNU/Linux Rolling
Release:        2022.2
Codename:       kali-rolling
Linux kali 5.16.0-kali7-amd64 #1 SMP PREEMPT Debian 5.16.18-1kali1 (2022-04-01) x86_64 GNU/Linux
but can you guys help me on this please

---

### Post by ramesh8 on 2022-05-29
[COLOR=#000000]Yes i am using kali .[/COLOR]
[COLOR=#000000]No LSB modules are available.Distributor ID: Kali[/COLOR]
[COLOR=#000000]Description: Kali GNU/Linux Rolling[/COLOR]
[COLOR=#000000]Release: 2022.2[/COLOR]
[COLOR=#000000]Codename: kali-rolling[/COLOR]
[COLOR=#000000]Linux kali 5.16.0-kali7-amd64 #1 SMP PREEMPT Debian 5.16.18-1kali1 (2022-04-01) x86_64 GNU/Linux[/COLOR]
[COLOR=#000000]but can you guys help me on this please[/COLOR]

---

### Post by deadflowr on 2022-05-29
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by ActionParsnip on 2022-05-29
Is Kali supported here? The kali forum is here
[https://forums.kali.org/](https://forums.kali.org/)

---

### Post by deadflowr on 2022-05-29
> Is Kali supported here?
In the most minimalistic way.
We allow some support, but we draw the line at any of kali's cracking tools.
We will not allow discussions about pentesting tools or cracking or tools used for cracking.

But questions unrelated to using those tools are usually fair game.

---

### Post by ramesh8 on 2022-05-29
OK got the point but i am right now at ubunutu same issue 
```
No LSB modules are available.


Distributor ID:    Ubuntu


Description:    Ubuntu 22.04 LTS


Release:    22.04


Codename:    jammy


Linux test-VirtualBox 5.15.0-33-generic #34-Ubuntu SMP Wed May 18 13:34:26 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```


Here's the error i am getting 

```
sudo make install


if test -d ./.hg && cd .; then \


    if hg log --style=changelog -b default > ChangeLog.tmp; then \


	mv -f ChangeLog.tmp ChangeLog; \


    else \


	rm -f ChangeLog.tmp; \


    fi; \


elif test -d ./.git && cd .; then \


    ./log2cl.pl -b master > ChangeLog; \


else \


    echo "ChangeLog data not available" > ChangeLog; \


fi


for d in lib/util  plugins/group_file plugins/sudoers plugins/system_group src include doc examples; do \


    (cd $d && exec make pre-install) && continue; \


    exit $?; \


done


make[1]: Entering directory '/home/test/Downloads/sudo-1.8.26/lib/util'


make[1]: Nothing to be done for 'pre-install'.


make[1]: Leaving directory '/home/test/Downloads/sudo-1.8.26/lib/util'


make[1]: Entering directory '/home/test/Downloads/sudo-1.8.26/plugins/group_file'


make[1]: Nothing to be done for 'pre-install'.


make[1]: Leaving directory '/home/test/Downloads/sudo-1.8.26/plugins/group_file'


make[1]: Entering directory '/home/test/Downloads/sudo-1.8.26/plugins/sudoers'


Checking existing sudoers file for syntax errors.


/bin/bash: line 3: ./visudo: No such file or directory


make[1]: *** [Makefile:384: pre-install] Error 127


make[1]: Leaving directory '/home/test/Downloads/sudo-1.8.26/plugins/sudoers'


make: *** [Makefile:103: pre-install] Error 2

```

I downloaded the files for 1.8.26 version from here [https://www.sudo.ws/getting/download/](https://www.sudo.ws/getting/download/) then i ran this following command ./configure , make , then make install and it is getting while runnng make install i want to overwrite the current version of sudo

---

