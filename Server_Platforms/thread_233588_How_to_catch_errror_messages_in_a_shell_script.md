---
title: "How to catch errror messages in a shell script?"
date: 2006-08-10
forum: Server Platforms
---

### Post by djvishnu on 2006-08-10
I need some help finding out how to catch error messages from commands in a shell script.

I am writing an web based network management tool for a broadband company, where i run alot of shell commands from php scripts. I want to print out the error messages if there are any, but I have no idea how to do it. PHP ony catches stdout.

To illustrate the problem, try this:
```
0 vishnu@helmsdeep:~> fping 10.0.15.251 -c 3
10.0.15.251 : [0], 84 bytes, 0.66 ms (0.66 avg, 0% loss)
10.0.15.251 : [1], 84 bytes, 0.63 ms (0.64 avg, 0% loss)
10.0.15.251 : [2], 84 bytes, 0.63 ms (0.64 avg, 0% loss)

10.0.15.251 : xmt/rcv/%loss = 3/3/0%, min/avg/max = 0.63/0.64/0.66

```

No problem there. If you try to put the output into a file this happens:
```
0 vishnu@helmsdeep:~> fping 10.0.15.251 -c 3 > hei

10.0.15.251 : xmt/rcv/%loss = 3/3/0%, min/avg/max = 0.62/0.63/0.65
0 vishnu@helmsdeep:~> cat hei
10.0.15.251 : [0], 84 bytes, 0.62 ms (0.62 avg, 0% loss)
10.0.15.251 : [1], 84 bytes, 0.64 ms (0.63 avg, 0% loss)
10.0.15.251 : [2], 84 bytes, 0.65 ms (0.63 avg, 0% loss)

```

The last line that prints the status summary is printed to somewhere else then stdout. Where? stderr? How can i catch this? Be shell specific, if I can get it working there I can manage the php bit.

Btw, should i have posted this in one of the other forums?

---

### Post by xtacocorex on 2006-08-10
> **djvishnu said:**
> I need some help finding out how to catch error messages from commands in a shell script.

I am writing an web based network management tool for a broadband company, where i run alot of shell commands from php scripts. I want to print out the error messages if there are any, but I have no idea how to do it. PHP ony catches stdout.

To illustrate the problem, try this:
```
0 vishnu@helmsdeep:~> fping 10.0.15.251 -c 3
10.0.15.251 : [0], 84 bytes, 0.66 ms (0.66 avg, 0% loss)
10.0.15.251 : [1], 84 bytes, 0.63 ms (0.64 avg, 0% loss)
10.0.15.251 : [2], 84 bytes, 0.63 ms (0.64 avg, 0% loss)

10.0.15.251 : xmt/rcv/%loss = 3/3/0%, min/avg/max = 0.63/0.64/0.66

``` 
No problem there. If you try to put the output into a file this happens:
```
0 vishnu@helmsdeep:~> fping 10.0.15.251 -c 3 > hei

10.0.15.251 : xmt/rcv/%loss = 3/3/0%, min/avg/max = 0.62/0.63/0.65
0 vishnu@helmsdeep:~> cat hei
10.0.15.251 : [0], 84 bytes, 0.62 ms (0.62 avg, 0% loss)
10.0.15.251 : [1], 84 bytes, 0.64 ms (0.63 avg, 0% loss)
10.0.15.251 : [2], 84 bytes, 0.65 ms (0.63 avg, 0% loss)

``` 
The last line that prints the status summary is printed to somewhere else then stdout. Where? stderr? How can i catch this? Be shell specific, if I can get it working there I can manage the php bit.

Btw, should i have posted this in one of the other forums?

Have you tried to add the following to the command?
```
fping 10.0.15.251 -c 3 &> hei
```
This will send stdout and stderr to the same file. For more reference: [http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)

Hope this helps.

---

### Post by djvishnu on 2006-08-10
Thank You!

:)

---

