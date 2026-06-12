---
title: "On boot, black screen says &quot;Ubuntu 12.04 LTS ubuntu tty1&quot;"
date: 2016-07-01
forum: Virtualisation
---

### Post by rami0786 on 2016-07-01
hello everyone...
i'm a computer science student, and in one of my courses we using ubuntu on virtual machine (VMware palyer)
the os version is 12.04 and it always ask for upgrade and i delay it, until last night, after the update the machine wouldn't starts,
i got message "ubunto 12.04 LTS ubuntu tty1


                     ubuntu login: mountall: Disconnected from plymoth"
and i have no clue what to do...
any suggestions,?!!!
p.s please explain step by step because i dont usualy use linux.

i want to add two pictures that might help speed up the process.
[https://drive.google.com/file/d/0B47s1MMwtfdbY0JZcExud24yM3c/view?usp=sharing](https://drive.google.com/file/d/0B47s1MMwtfdbY0JZcExud24yM3c/view?usp=sharing) [IMG]https://drive.google.com/file/d/0B47s1MMwtfdbY0JZcExud24yM3c/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/0B47s1MMwtfdbYUJBclZ6Z2lxYXc/view?usp=sharing](https://drive.google.com/file/d/0B47s1MMwtfdbYUJBclZ6Z2lxYXc/view?usp=sharing) [IMG]https://drive.google.com/file/d/0B47s1MMwtfdbYUJBclZ6Z2lxYXc/view?usp=sharing[/IMG]

---

### Post by howefield on 2016-07-01
Thread moved to the "*Virtualisation*" forum.

---

### Post by MAFoElffen on 2016-07-02
At the command prompt, enter your username and password (your credentials).

Then copy down the results of this command:
```

lst -l ~/.Xauthority

```
please post that here within code tags.

Since you are a student learning Linux(?). I'll explain. The above command checks for the presence, set privileges and ownership of your own .Xauthority file located in your home directory.

That file should be there, owned by you and have you should have both read and write permissions.

xauth helps enforce access controls in XSession display.. The .Xauthority file contains a 'key' for the present user of that hostname. Some other version of Linux have a mkxauth utilty for creating an .Xauthority file. Ubuntu does not., so have to do that manually... except if you use this script (which would do the same as mkxuath):
```

#!/bin/bash
## mafoelffen 2016.07.01, mkxauth
# Syntax: mkxauth <UserName>

UserName=$1

if [[ -n "$UserName" ]]; then
    if [[ -f ~/.Xauthority ]]; then 
        rm /home/($UserName)/.Xauthority # remove if old is there. It may be corrupted or have an old or incorrect authorization key.
    else
        echo "Users Xautority file did not exist."
    fi
    touch /home/($UserName)/.Xauthority # create the file
    chmod 600  /home/($UserName)/.Xauthority # set the permissions of the file
    chown $UserName  /home/($UserName)/.Xauthority # set the ownership to the user
    echo "New Xauthority file created" # tell the user if successful
else
    echo "Argument Error. No username given"
fi

```
Put that into a file named mkxauth. Make it executable.
```

chmod +x mkxauth

```
Or just do the commands manually. 

Say, if your user name is "sam", or you are an admin setting this up for user "sam"... Then the syntax would be
```

mkxauth sam

```
To others, later, I'll post this script as a downloadable attachment in my Graphics Resolution Sticky and link it from Post #2.

---

### Post by rami0786 on 2016-07-02
i typed the second code and the output was "[COLOR=#000000][FONT=&amp]Xautority file did not exist"
[/FONT][/COLOR]screenshot:
[https://drive.google.com/file/d/0B47s1MMwtfdbTVlieGg1U0JZMW8/view?usp=sharing](https://drive.google.com/file/d/0B47s1MMwtfdbTVlieGg1U0JZMW8/view?usp=sharing)
p.s. the other codes don't work.
plus, here is screenshot for the use of the first code:
[https://drive.google.com/file/d/0B47s1MMwtfdbdTBZQUtpa2N3Y00/view?usp=sharing](https://drive.google.com/file/d/0B47s1MMwtfdbdTBZQUtpa2N3Y00/view?usp=sharing)

---

### Post by MAFoElffen on 2016-07-02
If you are going to type it in manually, then:
```

 rm ~/.Xauthority
 touch ~/.Xauthority
 chmod 600  ~/.Xauthority
 chown YourUserName ~/.Xauthority    # <-- substitute your own user name in place of YourUserName

```

---

