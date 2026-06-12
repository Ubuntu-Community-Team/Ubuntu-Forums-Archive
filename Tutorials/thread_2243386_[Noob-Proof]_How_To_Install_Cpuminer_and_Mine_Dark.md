---
title: "[Noob-Proof] How To Install Cpuminer and Mine Darkcoin under Linux/Ubuntu"
date: 2014-09-08
forum: Tutorials
---

### Post by GreenRaccoon on 2014-09-08
Here's a *THOROUGH* guide to set up cpuminer and mine darkcoin. Basically, I've done most of the thinking for you already; you mostly just have to copy and paste. :biggrin: This should work for Ubuntu, Xubuntu, Linux Mint, etc.

**1-** Check if your processor supports the new AES-NI instruction sets. You can do this one of two ways (Method A is easier if you know the model of your processor):
[LIST]
[*]Method A
-If your processor is listed on this page, it supports the AES-NI instruction set: 
[http://ark.intel.com/search/advanced/?AESTech=true](http://ark.intel.com/search/advanced/?AESTech=true)
[*]Method B
-Run this command in Terminal:
```
grep aes /proc/cpuinfo
```
--[COLOR=#800000]If nothing shows up[/COLOR], your processor [COLOR=#800000]DOESN'T support [/COLOR]the [COLOR=#800000]AES-NI[/COLOR] instruction set.
--If you [COLOR=#006400]DO[/COLOR] see line(s) containing the word "[COLOR=#006400]aes[/COLOR]", your processor [COLOR=#006400]DOES support[/COLOR] the [COLOR=#006400]AES-NI[/COLOR] instruction set.
[/LIST]
**2-** [COLOR=#006600]If your processor supports [/COLOR][COLOR=#000000]the [/COLOR][COLOR=#006600]AES-NI[/COLOR] instruction set, [COLOR=#006600]jump to [post two]("http://ubuntuforums.org/showthread.php?t=2243386&p=13117765#post13117765")[/COLOR] [COLOR=#000000]of this thread. If it [/COLOR][COLOR=#800000]doesn't[/COLOR][COLOR=#000000], just [/COLOR][COLOR=#800000]keep following this post[/COLOR][COLOR=#000000].[/COLOR]

[B][U]For processors that [COLOR=#800000]DON'T[/COLOR] support AES-NI

[/U][/B][I](I uploaded a script at the bottom of this post that will run steps 3-10 for you. To run it, run this command:
"cd ~/Downloads && chmod +x install-cpu*.sh && sh install-cpu*.sh")[/I]
*(The regular one is for Ubuntu, but I've also uploaded one for Arch Linux.)*

**3**- **Update** your computer and **install dependencies**. Open up Terminal with ctrl+alt+t. Then copy (ctrl+c) and paste (ctrl+SHIFT+v) this:
```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install -y git curl unzip gedit automake autoconf dh-autoreconf build-essential pkg-config openssh-server screen libtool libcurl4-openssl-dev libtool libncurses5-dev libudev-dev
```

**4-** **Download** version 1.2c of **cpuminer** (this version is best for processors that DON'T support the AES-NI instruction set)
```
cd ~
git clone https://github.com/ig0tik3d/darkcoin-cpuminer-1.2c.git
```
**5-** **Install cpuminer** (compile, make, and install)
```
cd ~/darkcoin-cpuminer-1.2c
chmod +x autogen.sh
./autogen.sh
./configure CFLAGS="-O3"
make
sudo make install
```
**6-** **Create** a **script **with this step. This script will run cpuminer with your mining preferences. It's pretty handy.
```
cd ~
gedit darkcpu
```
**7-** An empty file should pop up. **Copy and paste** this in there:
```
#!/bin/bash
cd ~/darkcoin-cpuminer-1.2c
./minerd -a X11 -o # -u # -p #
```
**8-** Don't close the file yet. First **replace the "#" signs** with what you need. If you have no idea what to put for "#", keep reading. If you know what to put, then skip to step 8.
[LIST]
[*]"-a" stands for "**algorithm**." You'll always want [COLOR=#006600]X11[/COLOR]. Don't change this.
[*]"-o" stands for your **pool's address and port**. "[COLOR=#006600]stratum+tcp://address.com:####[/COLOR]" Find that on your pool's website (usually under "Help" and then "Getting started"). If you don't have a pool yet, here's a list: [https://www.darkcoin.io/mining.html](https://www.darkcoin.io/mining.html) This is what mine is:
```
./minerd -a X11 -o stratum+tcp://mine1.coinmine.pl:16090
```
[*]"-u" stands for your personal **username** that you use to login on your pool's website. BUT "-u" also includes a worker name that you have to create on your pool's website. The format looks like this: “[COLOR=#006600]-u username.worker[/COLOR]”. On your pool's website, you can have ONE username but MANY different workers. Think of it this way. The "username" represents "you" and the "workers" are the "slaves" that work for you. :shock: Your username identifies you, and each worker represents each computer/processor that's mining for you. If you haven't created a worker on your pool's website, do that now.

So if the username on my pool is "GreenRaccoon23," and I created a worker on there named "chucknorris," it would look like this:
```
 ./minerd -a X11 -o stratum+tcp://mine1.coinmine.pl:16090 -u GreenRaccoon23.chucknorris
```
[*]"-p" stands for your **password**: your WORKER'S password, NOT your username's password. You set this up on your pool's website.

So if the password for my worker "chucknorris" is "knowsvictoriassecret," this is what it would look like:
```
./minerd -a X11 -o stratum+tcp://mine1.coinmine.pl:16090 -u GreenRaccoon23.chucknorris -p knowsvictoriassecret
```
[*]Here's the basic format for the whole line:
```
./minerd -a X11 -o stratum+tcp://your.pool.address:port -u username.worker -p password
```
Here's an example format for the whole file:
```
#!/bin/bash
cd ~/darkcoin-cpuminer-1.2c
./minerd -a X11 -o stratum+tcp://mine1.coinmine.pl:16090 -u GreenRaccoon23.chucknorris -p knowsvictoriassecret
```
[/LIST]
**9- Save** the file and **close** it.
**10-** **Make **the script **executable **with this command:
```
chmod +x darkcpu
```

[B]_Run cpuminer_
11-[/B] Running cpuminer is easy once you've made the "darkcpu" script explained above. Just **change directory** to your home folder and **run the script**:
```
cd ~
./darkcpu
```
**12-** Now you're making currency by doing nothing. :cool: When you want to stop it, press "ctrl+c". To run it again, repeat step 11. To change cpuminer's settings, go through steps 6-9 again.

*(If you want to install sgminer for GPU mining also, I have another guide: [http://ubuntuforums.org/showthread.php?t=2243387](http://ubuntuforums.org/showthread.php?t=2243387))*

---

### Post by GreenRaccoon on 2014-09-08
[B][U]For processors that [COLOR=#006400]DO[/COLOR] support AES-NI

[/U][/B]*(I uploaded a script at the bottom of this post that will run steps 3-10 for you. *[I]To run it, run this command:
"cd ~/Downloads && chmod +x install-cpu*.sh && sh install-cpu*.sh"[/I][I])
(The regular one is for Ubuntu, but I've also uploaded one for Arch Linux.)[/I][B]

**3**- **Update** [/B]your computer and **install dependencies**. Open up Terminal with ctrl+alt+t. Then copy (ctrl+c) and paste (ctrl+SHIFT+v) this:
```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install -y git curl unzip gedit automake autoconf dh-autoreconf build-essential pkg-config openssh-server screen libtool libcurl4-openssl-dev libtool libncurses5-dev libudev-dev
```
**4- Download** version 1.3 of **cpuminer** (this version is best for processors that DO support the AES-NI instruction set)
```
cd ~
git clone https://github.com/elmad/darkcoin-cpuminer-1.3-avx-aes.git
```
**5- Install cpuminer** (compile, make, and install)
```
cd ~/darkcoin-cpuminer-1.3-avx-aes
chmod +x autogen.sh
./autogen.sh
./configure CFLAGS="-O3 -march=native"
make
sudo make install
```
**6- Create** a **script** with this step. This script will run cpuminer with your mining preferences. It's pretty handy.
```
cd ~
gedit darkcpu
```
**7- **An empty file should pop up. **Copy and paste** this in there:
```
#!/bin/bash
cd ~/darkcoin-cpuminer-1.3-avx-aes
./minerd -a X11 -o # -u # -p #
```
**8-** Don't close the file yet. First **replace the "#" signs** with what you need. If you have no idea what to put for "#", keep reading. If you know what to put, then skip to step 8.
[LIST]
[*]"**-a**" stands for "**algorithm**." You'll always want [COLOR=#006600]X11[/COLOR]. Don't change this.
[*]"**-o**" stands for your **pool's address and port**. "[COLOR=#006600]stratum+tcp://address.com:####[/COLOR]" Find that on your pool's website (usually under "Help" and then "Getting started"). If you don't have a pool yet, here's a list: [https://www.darkcoin.io/mining.html](https://www.darkcoin.io/mining.html) This is what mine is:
```
./minerd -a X11 -o stratum+tcp://mine1.coinmine.pl:16090
```
[*]"**-u**" stands for your personal **username** that you use to login on your pool's website. BUT "-u" also includes a worker name that you have to create on your pool's website. The format looks like this: &#8220;[COLOR=#006600]-u username.worker[/COLOR]&#8221;. On your pool's website, you can have ONE username but MANY different workers. Think of it this way. The "username" represents "you" and the "workers" are the "slaves" that work for you. :eek: Your username identifies you, and each worker represents each computer/processor that's mining for you. If you haven't created a worker on your pool's website, do that now.

So if the username on my pool is "GreenRaccoon23," and I created a worker on there named "chucknorris," it would look like this:
```
 ./minerd -a X11 -o stratum+tcp://mine1.coinmine.pl:16090 -u GreenRaccoon23.chucknorris
```
[*]"**-p**" stands for your **password**: your WORKER'S password, NOT your username's password. You set this up on your pool's website.

So if the password for my worker "chucknorris" is "knowsvictoriassecret," this is what it would look like:
```
./minerd -a X11 -o stratum+tcp://mine1.coinmine.pl:16090 -u GreenRaccoon23.chucknorris -p knowsvictoriassecret
```
[*]Here's the **basic format** for the whole line:
```
./minerd -a X11 -o stratum+tcp://your.pool.address:port -u username.worker -p password
```
Here's an **example** of the whole file:
```
#!/bin/bash
cd ~/darkcoin-cpuminer-1.3-avx-aes
./minerd -a X11 -o stratum+tcp://mine1.coinmine.pl:16090 -u GreenRaccoon23.chucknorris -p knowsvictoriassecret
```
[/LIST]
**9- Save** the file and **close** it.
**10-** **Make** the script **executable** by running this:
```
chmod +x darkcpu
```

[B]_Run cpuminer_
11-[/B] Running cpuminer is easy once you've made the "darkcpu" script explained above. Just **change directory** to your home folder and **run the script**:
```
cd ~
./darkcpu
```
**12-** Now you're making currency by doing nothing. :cool: When you want to stop it, press "ctrl+c". To run it again, repeat step 11. To change cpuminer's settings, go through steps 6-9 again.

*(If you want to install sgminer for GPU mining also, I have another guide: [http://ubuntuforums.org/showthread.php?t=2243387](http://ubuntuforums.org/showthread.php?t=2243387))*

---

### Post by ann5 on 2014-09-28
whats the best a88x mobo that supports linux and would you recommend using linux mint mate over ubuntu to mine cpu coins thanks

---

### Post by GreenRaccoon on 2014-10-01
> **ann5 said:**
> whats the best a88x mobo that supports linux and would you recommend using linux mint mate over ubuntu to mine cpu coins thanks
I know for GPU's, the motherboard doesn't really affect mining speed. I'm not sure about CPU's though. If you're thinking of buying a new rig for mining, I'd highly suggest getting a GPU. To put it in perspective, my AMD A10-7850K APU (basically a CPU) gets about 500 kh/s, but my AMD Radeon 280x GPU gets over 2.5 Mh/s--5 times faster.

For darkcoin (and other x11 algorithm coins), the AMD 280x Radeon is hands-down the best value. It's almost as fast as the 290x but WAY cheaper.

Linux Mint Mate over Ubuntu? It won't matter much. I had problems with installing AMD GPU miners on Linux Mint XFCE for some weird reason, but for CPU mining, it won't matter much.

---

### Post by mariano.j on 2014-10-06
I am trying to compile [darkcoin-cpuminer-1.2c]("https://github.com/ig0tik3d/darkcoin-cpuminer-1.2c") on Ubuntu 14.04 following your instructions for a processor *not* supporting the AES-NI instruction set. I was getting a series of errors during make (step 5), starting with: 

```
error "SSE2 instruction set not enabled" 
```[INDENT] 
 [/INDENT]
(See [askubuntu]("http://askubuntu.com/questions/493038/error-compiling-the-darkcoin-miner-based-on-poolers-cpu-miner") for someone with the same problem on a Xubuntu 10.04 32 bit.) 

I enabled SSE2 as follows: 

  ```
$ ./configure CFLAGS="-O3 -msse2"
```

  configure then finishes without error, but make produces (among others): 

```
x6/grso-asm.c:6:3: error: unknown register name ‘%r15’ in ‘asm’ 
```[INDENT] 
 [/INDENT]
(See [bitcointalk]("https://bitcointalk.org/index.php?topic=421615.msg4823184#msg4823184") for someone with the same problem.) 

See [pastebin]("http://pastebin.com/dRm3FpNR") for full log. Do you have any idea how I could solve this, GreenRaccoon?

---

### Post by GreenRaccoon on 2014-10-08
> **mariano.j said:**
> I am trying to compile [darkcoin-cpuminer-1.2c]("https://github.com/ig0tik3d/darkcoin-cpuminer-1.2c") on Ubuntu 14.04 following your instructions for a processor *not* supporting the AES-NI instruction set. I was getting a series of errors during make (step 5), starting with: 

```
error "SSE2 instruction set not enabled" 
```[INDENT] 
 [/INDENT]
(See [askubuntu]("http://askubuntu.com/questions/493038/error-compiling-the-darkcoin-miner-based-on-poolers-cpu-miner") for someone with the same problem on a Xubuntu 10.04 32 bit.) 

I enabled SSE2 as follows: 

  ```
$ ./configure CFLAGS="-O3 -msse2"
```

  configure then finishes without error, but make produces (among others): 

```
x6/grso-asm.c:6:3: error: unknown register name ‘%r15’ in ‘asm’ 
```[INDENT] 
 [/INDENT]
(See [bitcointalk]("https://bitcointalk.org/index.php?topic=421615.msg4823184#msg4823184") for someone with the same problem.) 

See [pastebin]("http://pastebin.com/dRm3FpNR") for full log. Do you have any idea how I could solve this, GreenRaccoon?
Hm, I'd try running this:
```
sudo aptitude reinstall -r gcc gcc-multilib gcc-opt lib32gcc1 lib64gcc1 lib32gcc1-dbg lib64gcc1-dbg
```
What's your CPU, by the way? Could you paste the output of this please?
```
cat /proc/cpuinfo
```

---

### Post by probes88 on 2015-01-08
I installed the software -- but got stuck when filling out the gedit file. I don't know how to join the pool. I went to [http://mine1.coinmine.pl/#getting_started](http://mine1.coinmine.pl/#getting_started) but there is no where I see to create a username and worker name. How do I join a pool? Thanks.

---

### Post by gadha1998 on 2015-03-15
> **probes88 said:**
> I installed the software -- but got stuck when filling out the gedit file. I don't know how to join the pool. I went to [http://mine1.coinmine.pl/#getting_started](http://mine1.coinmine.pl/#getting_started) but there is no where I see to create a username and worker name. How do I join a pool? Thanks.

Are you still there? (at the issue?)

---

### Post by abnerfreitas on 2015-04-05
I have this output.

[2015-04-05 14:57:53] Starting Stratum on stratum+tcp://stratum.triplemining.com:3334
[2015-04-05 14:57:53] 2 miner threads started, using 'sha256d' algorithm.
[2015-04-05 14:57:53] Binding thread 0 to cpu 0
[2015-04-05 14:57:53] Binding thread 1 to cpu 1
[2015-04-05 14:57:53] ...retry after 1 seconds
[2015-04-05 14:57:54] ...retry after 1 seconds
[2015-04-05 14:57:56] ...retry after 1 seconds
[2015-04-05 14:57:57] ...retry after 1 seconds
[2015-04-05 14:57:58] ...retry after 1 seconds
[2015-04-05 14:57:59] ...retry after 1 seconds

Why the program don't start mining already?

---

