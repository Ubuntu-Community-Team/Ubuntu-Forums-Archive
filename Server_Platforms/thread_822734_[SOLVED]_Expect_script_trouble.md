---
title: "[SOLVED] Expect script trouble"
date: 2008-06-08
forum: Server Platforms
---

### Post by Road_Runner on 2008-06-08
Hi All,

This is my first post here although I have been browsing these forums for a while and found a lot of useful information :)

I am having trouble getting expect to work on my 8.04 server.  I have tried to create script to telnet into my router but expect just does not seem to work.  Here is my script:

#!/usr/bin/expect

set timeout 20 #If it all goes pear shaped the script will timeout after 20 seconds.

spawn telnet 192.168.1.1 #This spawns the telnet program
match_max 100000
expect -exact "Trying 192.168.1.1...\r
Connected to 192.168.1.1.\r
Escape character is '^]'.\r
VOYAGER2110 \r
Software Version: 3.03c\r
Login name: "
send -- "admin\r" #The script sends the user variable
expect -exact "admin\r
Password: "
send -- "**********\r" #The script sends the password variable
interact

When I try to run the script I get the following errors:

./expect_telnet.sh: line 6: spawn: command not found
./expect_telnet.sh: line 7: match_max: command not found
expect: invalid option -- e
usage: expect [-div] [-c cmds] [[-f] cmdfile] [args]
./expect_telnet.sh: line 15: send: command not found
expect: invalid option -- e
usage: expect [-div] [-c cmds] [[-f] cmdfile] [args]
./expect_telnet.sh: line 19: send: command not found
./expect_telnet.sh: line 20: interact: command not found

So it looks like expect is not working at all.

Any ideas on what the problem might be would be greatly appreciated.

Cheers

R_R

---

### Post by quelx on 2008-06-08
Try getting rid of unnecessary *match* info.  Also I think **\n** is the carriage return not **\r**.  Remove the spaces after the prompts. eg.

```
#!/usr/bin/expect -f
spawn telnet 192.168.1.1 #This spawns the telnet program
match_max 100000
expect -exact "Login name:"
send -- "admin\n" #The script sends the user variable
expect -exact "Password:"
send -- "**********\n" #The script sends the password variable
interact
```

---

### Post by Road_Runner on 2008-06-08
Thanks for the reply quelx.

I tried changing my code according to your post but I am still getting the same errors:

./expect_telnet.sh 
./expect_telnet.sh: line 6: spawn: command not found
./expect_telnet.sh: line 7: match_max: command not found
expect: invalid option -- e
usage: expect [-div] [-c cmds] [[-f] cmdfile] [args]
./expect_telnet.sh: line 15: send: command not found
expect: invalid option -- e
usage: expect [-div] [-c cmds] [[-f] cmdfile] [args]
./expect_telnet.sh: line 19: send: command not found
./expect_telnet.sh: line 20: interact: command not found

It just seems as though expect is not work at all for some reason?

---

### Post by quelx on 2008-06-08
did you change the first line?
```

#!/usr/bin/expect
``` to ```
#!/usr/bin/expect [COLOR="Red"]**-f**[/COLOR]
```

>  Expect  reads  cmdfile  for  a list of commands to execute.  Expect may
       also be invoked implicitly on systems which support the #! notation  by
       marking  the  script  executable,  and  making  the  first line in your
       script:

           #!/usr/bin/expect -f


---

### Post by Road_Runner on 2008-06-08
oops I missed the -f

Now I am getting the following error:
spawn telnet 192.168.1.1 #This spawns the telnet program
Usage: telnet [-4] [-6] [-8] [-E] [-L] [-a] [-d] [-e char] [-l user]
        [-n tracefile] [ -b addr ] [-r] [host-name [port]]
send: spawn id exp6 not open
    while executing
"send -- "admin\n" #The script sends the user variable"
    (file "./expect_telnet" line 8)

At least expect looks to be working now.

---

### Post by quelx on 2008-06-08
Remove the comments, **#blah blah blah**.  **expect** is sending them to **telnet** and telnet doesn't know what to do with them.

---

### Post by Road_Runner on 2008-06-08
Many thanks quelx.  It is working now :)

---

