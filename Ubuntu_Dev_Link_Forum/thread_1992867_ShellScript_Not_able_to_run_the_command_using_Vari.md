---
title: "ShellScript: Not able to run the command using Variable"
date: 2012-06-01
forum: Ubuntu Dev Link Forum
---

### Post by psrdotcom on 2012-06-01
Hi Folks,

I was trying to form a command using different variables and assigned to one variable including options.

Sample:

CMD="mount"

CMD=$CMD" /dev/sdb"

CMD=$CMD" /mnt/disk0/"

echo "The command is: $CMD"

$CMD

Output:
The command is: mount /dev/sdb /mnt/disk0
Error: No such file or directory:
""

Note: Both the /dev/sdb and /mnt/disk0 exists.

If I am running the same command without using variable from the script, it was working fine.

Please help me to get out of this problem.

---

### Post by Lars Noodén on 2012-06-01
You need to tell it to execute.  Try this:

```

$(echo $CMD)

```

Vaphell always has good solutions.  I hope he sees this thread.

---

### Post by psrdotcom on 2012-06-01
Hi,

Thanks for the reply.

But I have tried that as well. But I am getting error like CMD: command not found

I have put ${CMD}. That also didn't work.

Any other solution plz.

---

### Post by Lars Noodén on 2012-06-01
Yes, but you have to provide the full device name.  /dev/sdb is just a start, which partition on /dev/sdb are your trying to mount?  /dev/sdb1, /dev/sdb2, etc.?

---

### Post by psrdotcom on 2012-06-01
Hi,

Thanks for the quick reply.

I have put it as an example content.

Actually I was trying different command not the which is mentioned the thread.

I am displaying the command using just before running it.
It was the correct command.
I have copy and paste final command string in script and it was working fine.

What is the problem when I am using with variable.

ex:
echo ${CMD}
${CMD}

Output:
mount /dev/sdb1 /mnt/disk0
File not found error (When executing the command)

If I had placed the same command in script
mount /dev/sdb1 /mnt/disk0
It is executing perfectly.

Please let me know the solution.

---

### Post by psrdotcom on 2012-06-01
Solved it.

I have written the command to a temp file and executed the temp file with in the script.

---

### Post by bregma on 2012-06-03
You're looking for the 'eval' command.

For example,
```
$ **cmd="ls -l"**
$ **eval $cmd**
```

---

