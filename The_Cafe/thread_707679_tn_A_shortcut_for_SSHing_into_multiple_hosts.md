---
title: "tn: A shortcut for SSHing into multiple hosts"
date: 2008-02-25
forum: The Cafe
---

### Post by mssever on 2008-02-25
I SSH a lot. Back in the day (before I knew about SSH) I had the following in my ~/.alias: ```
alias tn='telnet somehost'
``` That alias eventually morphed to use SSH and the host involved has changed over the years.

Recently, though, I moved my websites over to nearlyfreespeech.net. That host creates a separate shell account for every domain and subdomain, so I was faced with typing lengthy username/hostname combinations every time I logged in. First, I started expanding my aliases, but then I thought better of it.

The result is attached. It's a shortcut to SSH and SCP to a number of hosts. For example, if you've configured foo to be an abbreviation for [EMAIL="bar@foo.baz.com"]bar@foo.baz.com[/EMAIL], then typing ```
tn foo
```will log you in. If you want to SCP some files, you can do something like ```
tn scp file1 file2 __HOST__:some/path/on/foo
```
You can also specify a default host, so that you can simply type 'tn' to SSH to your default host.

Uncompress tn.gz, make it executable (chmod 755 tn) and put it somewhete in your $PATH (such as /usr/local/bin). When you run tn the first time, it'll create its config file. Edit that file to set up your hosts. Once you've done that, you can run tn --help to see a short usage message.

Let me know what you think--or if you find any bugs. :)

---

