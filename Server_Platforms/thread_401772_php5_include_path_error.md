---
title: "php5 include_path error"
date: 2007-04-05
forum: Server Platforms
---

### Post by haloedrain on 2007-04-05
I just installed apache2 and php5.  Apache works great, but php is giving me a strange error every time I open a .php page: 

```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/pam/public_html/phpinfo.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```

I'd just get rid of that include_path line to see what happens, but I can't find it...  Any thoughts?

---

### Post by mssever on 2007-04-05
Does this error occur on **every** PHP page? If so, your PHP install must be messed up. The easiest thing would be to purge it (remove it completely) and reinstall php5. I hope you're using Synaptic, aptitude, or similar for this, as it works flawlessly for me.

---

### Post by haloedrain on 2007-04-05
Yeah, I get it on pages that contain nothing more than <?php echo 'test'; ?>.  I'll try purging and reinstalling php5 and see if it helps.

---

### Post by haloedrain on 2007-04-05
Well, I purged all of the php5 packages that I had installed and reinstalled php5, php5-common, and libapache-mod-php5 and I'm still getting the error.

An interesting complication is that I just installed apache and php5 on another computer and am getting the same error on a file that just has phpinfo() in it, but the file with echo 'test' works fine.  :confused:

---

### Post by mssever on 2007-04-05
Odd... looks like a permissions problem, but the error message isn't helpful enough to identify the problem. I really don't know what to tell you. Maybe someone else knows more about this than I do. Or maybe someone over at php.net knows something...

---

### Post by haloedrain on 2007-04-05
Omg.  Permissions.  I got distracted by the include_path thinking it was a conf problem (being that pear wasn't even installed) and did not even look at the individual file permissions.  All of the files I was testing were set so nothing could access them.  Easy fix, but man is that a terrible error message.

Thanks for the help!

---

### Post by mssever on 2007-04-05
Now I feel silly. That fatal error you got is just what you get when a require() fails. And PHP doubtless require()'s the file it's told to open. So the error message isn't so bad after all. It even identifies the file with the error. We both just failed to understand it.

---

### Post by haloedrain on 2007-04-05
Ah, ok, that makes sense :)

---

