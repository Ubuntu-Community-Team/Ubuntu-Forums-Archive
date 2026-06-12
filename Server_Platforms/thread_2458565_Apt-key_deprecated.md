---
title: "Apt-key deprecated"
date: 2021-02-27
forum: Server Platforms
---

### Post by richieserver on 2021-02-27
I am trying to add webmin gui to my server build, so I can access, but every time I keep using 

```

wget -q http://www.webmin.com/jcameron-key.asc -O- | apt-key add

```

I keep getting an error of 

> apt-key is deprecated

I have updated the OS but don't know how to get passed this

---

### Post by schragge on 2021-02-27
From [its manual page]("https://manpages.debian.org/unstable/apt/apt-key.8.en.html"):
> Use of **apt-key** is deprecated, except for the use of     **apt-key del** in maintainer scripts to remove existing keys from the     main keyring. If such usage of **apt-key** is desired the additional     installation of the GNU Privacy Guard suite (packaged in gnupg) is   required.

 [apt-key(8)]("https://manpages.debian.org/unstable/apt/apt-key.8.en.html") will last be available in Debian 11 and Ubuntu   22.04.

What you get is not an error, it's a warning.

It also looks like you forgot a dash:
```
wget -q http://www.webmin.com/jcameron-key.asc -O- | apt-key add -
```

---

### Post by richieserver on 2021-02-27
Hi there, thanks for your reply

When I typed the correction in, it now comes up with that the above can only be used by @root, which I got into the root by using su

Only to see that no valid PGP is found in the warning or error message
Same warning that the apt-key is deprecated

Warning also said that the keyring has to be managed by the files in trusted.gpg.d

There are two files in that folder

---

### Post by deadflowr on 2021-02-27
Here's some examples of the over the top methods to add keys in the future (currently):
[https://askubuntu.com/questions/1286545/what-commands-exactly-should-replace-the-deprecated-apt-key]("https://askubuntu.com/questions/1286545/what-commands-exactly-should-replace-the-deprecated-apt-key")

---

### Post by richieserver on 2021-02-27
I have renamed the teamviewer version to webmin, but it's still not working

---

### Post by ameinild on 2021-02-27
> **richieserver said:**
> I have renamed the teamviewer version to webmin, but it's still not working

Please explain this - what do you mean, where did Teamviewer come from?

---

### Post by schragge on 2021-02-27
From the Ask Ubuntu question linked to by **deadflowr**.

---

### Post by LHammonds on 2021-02-28
> **richieserver said:**
> I have updated the OS

So what version and kernel are you running?  You never clarified.

```
lsb_release -a
uname -a
```

LHammonds

---

### Post by CelticWarrior on 2021-02-28
> **schragge said:**
> From the Ask Ubuntu question linked to by **deadflowr**.
That question is about the same issue but related to a different certificate of a different software. **The outlined method is what you should follow, NOT download the Teamviewer's one and rename it**.

---

### Post by richieserver on 2021-02-28
> **CelticWarrior said:**
> That question is about the same issue but related to a different certificate of a different software. **The outlined method is what you should follow, NOT download the Teamviewer's one and rename it**.


I did follow the method with the Teamviewer's first, but that didn't anything

---

### Post by richieserver on 2021-02-28
> **LHammonds said:**
> So what version and kernel are you running?  You never clarified.

```
lsb_release -a
uname -a
```

LHammonds

I've attached pics because it's too much to type out

---

### Post by ameinild on 2021-03-01
I think the long-term solution here would be to create a script that:

[LIST]
[*]Checks if the key is ASCII-armored - and dearmor if that's the case 
[*]Put they key in your preferred folder (for instance /usr/share/keyrings) 
[*]Add the repo to your sources with the [signed-by=/usr/share/keyrings/<name-of-keyfile>] 
[/LIST]
I'm sure I'll eventually get around to creating that - and maybe LHammonds will as well - and maybe someone already did at some location I'm not aware of. ;)

---

### Post by ameinild on 2021-03-05
I created a shell script that can download and install keys to be used with [signed-by=] declaration in sources.list.

It's available on [github.com/ameinild/add-apt-key]("https://github.com/ameinild/add-apt-key").

Readme:
> 
# POSIX Script for installing APT keys
## General help
This script will help with installing PGP keys for APT repositories.

This script supports up to 2 arguments:
1st argument is input file. This can be either:
   - An URL - key will be downloaded into current path (using wget or curl)
    - A filename - reads an existing key in current path
    - A path and a filename - reads an existing key in given path
2nd argument is key output path and output name. This can be either:
    - Only filename - output path is set in config, saved as given filename
    - A path and a filename - output path is given here, saved as given filename
    - Only a path (end with /) - output path is given here, filename is taken from existing key
    - Empty - output path is set in config, filename is taken from existing key

This script has a config file `/usr/local/etc/add-apt-key.conf`, where the following variables can be set:
  - `keypath`   : path to store converted key - default is `/usr/share/keyrings`
  - `verbosity` : if set to Yes - displays extra output
  - `removetmp` : if set to Yes - remove input (non-converted) file

Example 1: (`PWD=/root`)

    sudo add-apt-key [https://mariadb.org/mariadb_release_signing_key.asc](https://mariadb.org/mariadb_release_signing_key.asc) /usr/local/share/keyrings/

Will download key in `/root`, convert it and store as `/usr/local/share/keyrings/mariadb_release_signing_key.gpg`

Example 2: (`PWD=/home/user`)

    sudo add-apt-key /root/mariadb_release_signing_key.asc /usr/local/share/keyrings/mariadbkey

Will use existing key in `/root`, convert it and store as `/usr/local/share/keyrings/mariadbkey.gpg`

Example 3: (`PWD=/home/user`)

    sudo add-apt-key mariadb_release_signing_key.asc mariadbkey

Will use existing key in `/home/user`, convert it and store as `/usr/share/keyrings/mariadbkey.gpg`

## Installation
Install by running the following commands:

    sudo curl -L [https://raw.githubusercontent.com/ameinild/add-apt-key/master/add-apt-key](https://raw.githubusercontent.com/ameinild/add-apt-key/master/add-apt-key) -o /usr/local/bin/add-apt-key
    sudo curl -L [https://raw.githubusercontent.com/ameinild/add-apt-key/master/add-apt-key.conf](https://raw.githubusercontent.com/ameinild/add-apt-key/master/add-apt-key.conf) -o /usr/local/etc/add-apt-key.conf
    sudo chmod a+rx /usr/local/bin/add-apt-key



---

### Post by richieserver on 2021-03-20
I will mark this as solved, as I've found another way to install webmin, though at the moment it isn't running, but I think I know why that is

---

