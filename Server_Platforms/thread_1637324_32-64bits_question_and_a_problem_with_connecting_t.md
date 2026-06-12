---
title: "32-64bits question and a problem with connecting to my server"
date: 2010-12-04
forum: Server Platforms
---

### Post by Aronnn on 2010-12-04
Hey,

When i wanted to install the 64bits version of ubuntu-server it gave me an error, it was something like this:
This kernel requires a x86-64CPU and you got a i686CPU.
I bought the server yesterday and this are the specifications:

HP DL380 G3
2 x 3.20 GHz / FSB 533 MHz / Cache 512KB
2 x 4 GB (2x 2048MB) DDR-266 PC-2100 ECC
73 GB 10K SCSI 3.5'' U320

So does this only support a 32bits version? because i got 8gb ram so that would be sad.

So after i saw it i installed the 32bits version and it is working but i got another question about it. I started a server with a .jar file but i cant connect to it. It is on the port 22003 and it is forwarded in the router. So why it is not working? Do i need to put something else on in the settings?

I hope you got enough information,
Aron

---

### Post by CharlesA on 2010-12-04
I would have thought a Xeon would be a 64-bit CPU, but the [spec sheet]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00459641&lang=en&cc=us&taskId=101&prodSeriesId=316529&prodTypeId=15351") doesn't say what model of Xeon it's running.

Can you run this:

```
cat /proc/cpuinfo
```

And post it inside [noparse]```

```[/noparse] tags please. :)

EDIT: Nevermind, I found a [forum post]("http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1291480660869+28353475&threadId=1440491") stating that it's 32-bit only.

If you are running the PAE kernel, it should be able to see all 8GB of memory.

---

### Post by Aronnn on 2010-12-04
It returns:

```
cpu family: 15
model: 2
model name: Intel(R) Xeon(TM) CPU 3.20GHz
cpu MHz: 3186.359
cache size: 1024KB
clflush size: 64
address size: 36 bits physical, 32 bits virtual
```

So does 32 bits virtual mean 32 bits? And i can only use 4gb ram now because i am unable to give away 5gb ram to my .jar file with:
```
java -Xmx5120M -Xms5120M -jar file.jar
```

So is there a solution to use all the ram or do i really need 64 bits for it?

Aron

---

### Post by CharlesA on 2010-12-04
Check under flags for "lm"

See [here](http://www.brandonhutchinson.com/Understanding_proc_cpuinfo.html).

You'd need a PAE kernel to address all 8GB.

Post this please:

```
uname -a
```

---

### Post by Aronnn on 2010-12-04
If i do uname -r it returns:
```
2.6.35-22-generic-pae
```

---

### Post by CharlesA on 2010-12-04
You are running the pae kernel.

Post this please:

```
free -m
```

Thanks.

---

### Post by Aronnn on 2010-12-04
free -m:
```
            Total      used      free      shared  buffers  cached
Mem:        7565       112       7453      0       11       66
-/+ buffers/cache:     34        7531
Swap:       2867       0         2867
```

---

### Post by CharlesA on 2010-12-04
It sees about 8GB. That server has an onboard video card, so you are good to go for that.

As for the port issue, can you verify that the process is actually listening on that port by running this:

```
netstat -ln
```

---

### Post by Aronnn on 2010-12-04
So it is just using 8gb ram? Because i can't reserve 5gb ram for java. So is this because ubuntu needs it or is it still not working?

---

### Post by CharlesA on 2010-12-04
You can't really "reserve" memory for a process, the OS will give a process as much memory as it needs.

---

### Post by Aronnn on 2010-12-04
Thanks alot,
One last question, if i use:
```
nohup java -jar server.jar
```
After i do this it will add it to nohup.out but i cant use another command. It just makes a blank line. So how do i run it and continue using other codes?

---

### Post by CharlesA on 2010-12-04
Should be able to just hit enter to get back to a normal prompt.

Otherwise, check out [screen]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/").

---

### Post by tgm4883 on 2010-12-04
I could be wrong on this, but I thought the pae kernel allowed the system to use > 4GB ram, but a single process could still only use up to 4GB.

:EDIT:

From wikipedia [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

```
 The 32-bit size of the virtual address is not changed, so regular application software continues to use instructions with 32-bit addresses and (in a flat memory model) is limited to 4 gigabytes of virtual address space. 
```

So no, you can't set java to use more than 4GB of ram with that. I can't believe they still make 32-bit only processors. Did you just buy that new? I'd return it and get something 64-bit

---

### Post by Aronnn on 2010-12-04
So now i got 4gb ram which i can use and 4gb ram which i cant use?

---

### Post by CharlesA on 2010-12-04
> **Aronnn said:**
> So now i got 4gb ram which i can use and 4gb ram which i cant use?

No. Only any one process can only use up to 4GB.

Personally, I'd return the server and buy one with a 64-bit CPU, but that's just me.

---

### Post by tgm4883 on 2010-12-04
> **Aronnn said:**
> So now i got 4gb ram which i can use and 4gb ram which i cant use?

Incorrect, as CharlesA and I said. A single process can only use up to 4GB of RAM. That doesn't mean that 4GB go to waste, that means that one process can use 4GB of RAM. If you have other processes running on the machine, they can use 4GB of ram too.

You could have 2 processes each using 4GB of RAM each with PAE, without PAE you can't do that.

I'd return the server though and get one that supports 64-bit

---

