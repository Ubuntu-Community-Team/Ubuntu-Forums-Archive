---
title: "Upload scp auto resume help"
date: 2010-01-05
forum: Server Platforms
---

### Post by dragos2 on 2010-01-05
I have a compressed backup that I want to crypt and upload to a remote server through
ssh once in a while.

The problem is with the size, more than 4 GB. If the connection drops how does scp know to resume? This should be an automated process.

I need some help on this please :)

---

### Post by kiranmurari on 2010-01-05
[SIZE=2]You can acheive this using rsync. But you need to have rsync on the remote host.
Add the follwoing line to your shell's startup script (ex: if you use bash, add
to ~/.bashrc script)
[/SIZE]
```
alias scpresume="rsync --partial --progress --rsh=ssh"
```[SIZE=2]rsync communication is not secure by default, so we use tunneling to achieve secure communication (by using --rsh=ssh)[/SIZE]
       [SIZE=2]Now you can use **scpresume** command to copy the file to the remote machine.[/SIZE]
       [SIZE=2]
[/SIZE]
[SIZE=2]Hope this helps[/SIZE]
       [SIZE=2]
[/SIZE]
[SIZE=2]Regards,
Kiran[/SIZE]

---

### Post by BkkBonanza on 2010-01-05
Rsync can run over ssh just like scp. It is secure that way, of course.
Use a command like,

rsync -vztpre "ssh -p <port>"  path_to_files user@host:/path_to_put_files

Rsync is the way to go because it will continue from where it stopped if cut off (and assuming you set up some way to retry during a failure). You only need the port value above if ssh is listening on a port other than 22. Doing it this way requires no rsync server at the other end as ssh will start rsync to handle the data.

---

### Post by dragos2 on 2010-01-06
> **BkkBonaza said:**
> Rsync can run over ssh just like scp. It is secure that way, of course.
Use a command like,

rsync -vztpre "ssh -p <port>"  path_to_files user@host:/path_to_put_files

Rsync is the way to go because it will continue from where it stopped if cut off (and assuming you set up some way to retry during a failure). You only need the port value above if ssh is listening on a port other than 22. Doing it this way requires no rsync server at the other end as ssh will start rsync to handle the data.

Thank you both for solutions, I am trying this one now.

Is there a way to see a progress during upload?

---

### Post by BkkBonanza on 2010-01-06
Yes, -P will show file progress and -v will show info about state and overall progress.
See "man rsync" for everything.

---

### Post by dragos2 on 2010-01-06
> **BkkBonaza said:**
> Yes, -P will show file progress and -v will show info about state and overall progress.
See "man rsync" for everything.

Thanks.

One last thing, how can I make it start over if the connecrtion drops?
I was thinking of a bash script that will run the command until it returns 0 - success.

Any idea of what is the correct status code in case of success and how to get it from bash script ?

---

### Post by BkkBonanza on 2010-01-06
The rsync error codes are in the man info, near the end.
As per most programs a return value of 0 means success. Rsync will return other codes to indicate various errors.

You can write a script that loops on rsync until it gets a exit code of 0 and then ends. If you do that I'd suggest putting a sleep command in the loop so there is a modest delay between attempts otherwise you can end up in some nasty behavior and giving a small pause between retries allows for the problem that broke the connection to get resolved.

Use the $? variable after the rsync to detect the last return code.
eg.

```
rsync blah blah
while [ $? != 0 ]; do
  sleep 60
  rsync blah blah
done
```

---

### Post by dragos2 on 2010-01-06
> **BkkBonaza said:**
> The rsync error codes are in the man info, near the end.
As per most programs a return value of 0 means success. Rsync will return other codes to indicate various errors.

You can write a script that loops on rsync until it gets a exit code of 0 and then ends. If you do that I'd suggest putting a sleep command in the loop so there is a modest delay between attempts otherwise you can end up in some nasty behavior and giving a small pause between retries allows for the problem that broke the connection to get resolved.

Use the $? variable after the rsync to detect the last return code.
eg.

```
rsync blah blah
while [ $? != 0 ]; do
  sleep 60
  rsync blah blah
done
```


Thank you very much, it seems to be what I need :)

Now I only need to restrict the autherized_keys from one host and this particular command:
Something like this on the backup server:
```

from="someserver.subdomain.com",no-X11-forwarding,noagent-forwarding ssh-rsa
command="rsync -vvztPre "ssh -p 22" /localfile user@server:/remote/path
" AAAAC4MybC1yc2EAAAABIwAAAQEAybmcqaU/Xos/GhYCzkV+kDsK8+A5OjaK5WgLMqm
u38aPo56Od10RQ3EiB42DjRVY8trXS1NH4jbURQPERr2LHCCYq6tHJYfJNhUX/COwHs
+ozNPE83CYDhK4AhabahnltFE5ZbefwXW4FoKOO+n8AdDfSXOazpPas8jXi5bENf7he
ZT++a/Qxbu9JHF1huThuDuxOtIWl07G+tKqzggFVknM5CoJCFxaik91lNGgu2OTKfY9
4c/ieETOXE5L+fVrbtOh7DTFMjIYAWNxy4tlMR/59UVw5dapAxH9J2lZglkj0w0LwFI
+7hZu9XvNfMKMKg+ERAz9XHYH3608RL1RQ== This comment describes key #2

```
I just hope it will work, do you have any suggestions on this ?

---

### Post by BkkBonanza on 2010-01-06
I haven't used the client limiting functions tied to the key but no reason it shouldn't work as long as the syntax is correct. Probably a good way to tighten up security.

---

