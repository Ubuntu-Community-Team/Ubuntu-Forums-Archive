---
title: "Little scripting question"
date: 2011-06-01
forum: The Cafe
---

### Post by Jensss on 2011-06-01
Probably a silly question.
I'm making a script and want to ls -l a variable.

so:

```
read -p "What is your variable?" var
ls -l $var

```

How to get this work?
When I do it like this i get the ls -l from the pwd...

---

### Post by wojox on 2011-06-01
You would echo $var

```
echo $var
```

---

### Post by Jensss on 2011-06-01
> **wojox said:**
> You would echo $var

```
echo $var
```

I don't want to see the $var..
I want to see the output of "ls -l $var"
Where $var is for example /etc ...

---

### Post by wojox on 2011-06-01
Oh. So something like:

```
read -p "What directory do want to list?" var
```

```
/etc
```

```
ls -l $var
```

---

### Post by Jensss on 2011-06-01
> **wojox said:**
> Oh. So something like:

```
read -p "What directory do want to list?" var
```

```
/etc
```

```
ls -l $var
```

I quote myself from the fipo: When I do it like this i get the ls -l from the p(resent)w(working)d(irectory)...

---

### Post by qyot27 on 2011-06-01
Are you using #!/bin/sh or #!/bin/bash?  But for the record, the following script:

```
#!/bin/bash -x
read -p "What directory?" var
ls -l $var
```
Listed the contents of whatever directory I told it to.

It should also work correctly if one issues this command as a standalone in a regular Terminal window:
```
read -p "What directory?" var && ls -l $var
```
In which case, it should ask for your variable, and then print accordingly.  If it doesn't work in the script but it does in the Terminal, then you're likely hitting the problem I describe below.

I have noticed that certain things may be acceptable to bash, but not sh - I was trying to make one of my scripts cross-platform, and while MSys uses bash regardless of whether sh or bash is declared, I had trouble when trying to get it to work on Ubuntu.  The solution?  Change 'sh' to 'bash'.  Then it worked fine.

---

### Post by wojox on 2011-06-01
> **Jensss said:**
> I quote myself from the fipo: When I do it like this i get the ls -l from the p(resent)w(working)d(irectory)...

Really, I tried it and when I store the /etc value in my $var it works fine.

---

