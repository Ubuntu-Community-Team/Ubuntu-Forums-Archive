---
title: "Many errors found using ClamAV"
date: 2016-02-05
forum: Security
---

### Post by helm10101 on 2016-02-05
I scanned my whole computer using clamscan -r /, 
and I got 0 infected files, however found "Total errors: 23007" 
What does that mean?

---

### Post by matt_symes on 2016-02-05
Hi

You may want to post some of the errors or, at best, we'll just be guessing.

Kind regards

---

### Post by howefield on 2016-02-05
Files for which you do not have access permissions to (eg, system files or other users files) are reported as "errors".

They aren't real errors and can be ignored.

---

### Post by helm10101 on 2016-02-05
> **matt_symes said:**
> Hi

You may want to post some of the errors or, at best, we'll just be guessing.

Kind regards
It doesn't specify the errors on terminal, what command do I need in order to see?

> **howefield said:**
> Files for which you do not have access permissions to (eg, system files or other users files) are reported as "errors".

They aren't real errors and can be ignored.

Thanks :D

---

### Post by matt_symes on 2016-02-05
Hi

> **helm10101 said:**
> It doesn't specify the errors on terminal, what command do I need in order to see?

If it doesn't specify any specific error messages and you are running ClamAV under your own user from the root file system down, then howefield's post would detail the issue.

If you think this has answered your question then please mark this thread as SOLVED using the thread tools menu above post #1.

Kind regards

---

### Post by helm10101 on 2016-02-05
Before I mark as solved: So I ran ClamAV under my own user without giving it root permission, that's why it couldn't access some files, right?
So how can I tell ClamAV to scan all files with root permissions so it can scan those locations that were denied?

---

### Post by CharlesA on 2016-02-05
> **helm10101 said:**
> Before I mark as solved: So I ran ClamAV under my own user without giving it root permission, that's why it couldn't access some files, right?
So how can I tell ClamAV to scan all files with root permissions so it can scan those locations that were denied?

Why do you want to do the scan as a root user? Do you suspect you got an infection somewhere?

Normally, you would run the scan against your home directory (~) because the majority of threats clamav would pick up would come from the browser cache.

Clamav is used to detect Windows viruses and other unwanted junk, not Linux viruses.

---

### Post by helm10101 on 2016-02-05
I just want to learn some more commands because I'm new to Linux.
I know that they are not infected :), just want to see if it actually is going to make the 23000+ errors disappear.

---

### Post by SeijiSensei on 2016-02-05
```
sudo clamscan -rv /
```
will scan the entire directory structure and report on every file.  I suggest you run this instead:
```
sudo clamscan -rv / > clamscan.report 2>&1
```
which will send all the results to the file "clamscan.report" so you can review it at your leisure.

---

### Post by matt_symes on 2016-02-05
Hi

> **helm10101 said:**
> I just want to learn some more commands because I'm new to Linux.
I know that they are not infected :), just want to see if it actually is going to make the 23000+ errors disappear.

The are a number of files and directories outside of you home system that you cannot access unless you are using elevated privileges (in effect becoming the root user).

These are important system files that you should not be allowed to read.

There are a number of such files and directories in the /etc directory alone, such as the sudoers files and the directories containing some ssl certs.

As clamAV is running as your user, it can also not access these files and directories.

Here are some directories that my user cannot look into in the directory /etc.
```

matthew-xu-16-04:/home/matthew:0 % find /etc -type d -exec file '{}' 1>/dev/null +
find: &#8216;/etc/cups/ssl&#8217;: Permission denied
find: &#8216;/etc/ssl/private&#8217;: Permission denied
find: &#8216;/etc/polkit-1/localauthority&#8217;: Permission denied
matthew-xu-16-04:/home/matthew:0 %
```  

And here are some files that my user cannot read in that same directory (/etc).

```
matthew-xu-16-04:/home/matthew:0 % find /etc -type f -exec bash -c " [[ ! -r '{}' ]] && echo '{}'" \;
/etc/gufw/Office.profile
/etc/gufw/Public.profile
/etc/gufw/gufw.cfg
/etc/gufw/Home.profile
/etc/shadow
<snip>
```

This is a security feature and is exactly what you want.

Kind regards

---

### Post by helm10101 on 2016-02-05
Thank you matt !

---

### Post by matt_symes on 2016-02-05
Hi

If anyone's interested, a better command than 

```
find /etc -type f -exec bash -c " [[ ! -r '{}' ]] && echo '{}'" \;
```

would be

```
find /etc -type f ! -readable 2>/dev/null
```

or

```
find /etc -type f ! -perm -o+r 2>/dev/null
```

The last one does not check ACLs.

Just get find to check the permissions.

Kind regards

---

### Post by oldos2er on 2016-02-06
> **helm10101 said:**
> I just want to learn some more commands because I'm new to Linux.

Have a look at [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by helm10101 on 2016-02-06
> **oldos2er said:**
> Have a look at [http://linuxcommand.org/](http://linuxcommand.org/)

Thank you! :)

---

