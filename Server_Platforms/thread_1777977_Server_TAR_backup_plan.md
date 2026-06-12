---
title: "Server TAR backup plan"
date: 2011-06-08
forum: Server Platforms
---

### Post by pcarlos853 on 2011-06-08
Hi Everyone!,

I want to backup my Ubuntu 10.10 server. I am have set it up so it creates a tar file of a few directory's that I want to back up. The problem is I would like to have the tar file have a dynamic name (such as date & time) vs what I currently have which is a static name that gets overwritten daily. Is it posible to use the tar command to create a dynamic name? Then I have the backup files sent to an other ubuntu 10.10 server via ssh and cron jobs. Is there a better way to backup a few directorys?

Thanks!

---

### Post by Lars Noodén on 2011-06-08
That's what backticks (**`**) are for:

```

[s]tar zcf "`date +"%Y-%m-%d-%H:%M"`.tar.gz" */path/to/some/dir/to/be/tarred*[/s]
tar zcf "`date +"%Y-%m-%d-%H%M"`.tar.gz" */path/to/some/dir/to/be/tarred*

```

---

### Post by pcarlos853 on 2011-06-08
Cool! I never know I could do that in a tar command! 

Thanks!

---

### Post by pcarlos853 on 2011-06-08
Hi!,

I just tried the command and am having some problems. 

Command:
tar zcf "`date +"%Y-%m-%d-%H:%M"`.tar.gz" /var/www2

Output:
tar: Removing leading `/' from member names
tar (child): Cannot connect to 2011-06-08-13: resolve failed
tar: 2011-06-08-13\:52.tar.gz: Cannot write: Broken pipe
tar: Error is not recoverable: exiting now

Any ideas what I am doing wrong?

Thanks!

---

### Post by Lars Noodén on 2011-06-08
It was my mistake.  Bash didn't like the colon.  Rather than try a way around it, the fast way is just remove it or to use a dash instead:

```

tar zcf "`date +"%Y-%m-%d-%H%M"`.tar.gz" /path/to/some/dir/to/be/tarred

```

There are more choices about the [date](http://manpages.ubuntu.com/manpages/natty/en/man1/date.1.html) format.

---

### Post by pcarlos853 on 2011-06-08
Removing the : worked.

Thanks!

---

