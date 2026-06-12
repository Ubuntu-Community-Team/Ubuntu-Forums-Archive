---
title: "Need help with Alias/function preventing &quot;sudo reboot&quot;?"
date: 2008-09-24
forum: Server Platforms
---

### Post by djvishnu on 2008-09-24
I want to make an alias/function that asks the user
"are you sure (y/n)?" when "sudo reboot" is called.

I have restarted wrong computer enough times to finally try to do something about this :)

I've come this far:
```
read -p "really reboot? (y/n)?"
if [ $REPLY != "y" ]; then
     echo "thought so..."
     exit 1
fi
reboot
```

but I have no idea on how to make this "global" - for all users. I cant rename /sbin/reboot - seems the os uses it as well.

---

### Post by ilrudie on 2008-09-24
you could try adding it to the /etc/bash.bashrc file.

---

### Post by djvishnu on 2008-09-24
> **ilrudie said:**
> you could try adding it to the /etc/bash.bashrc file.


I tried adding a function, and kinda worked: the function executes, however, when i do "sudo functionname" i get "command not found"

---

### Post by Krupski on 2008-09-24
> **djvishnu said:**
> I tried adding a function, and kinda worked: the function executes, however, when i do "sudo functionname" i get "command not found"

Executable stuff (scripts or binary) must either be explicitly called or else they must be in the path. The script must also be set as executable (i.e. chmod 0755).

For example, to run a script named "myscript.sh" in the current directory when that script is not in the path, do this:

```

./myscript.sh

```

Or, better, put the executable file into a directory that's in the path. Find out the path like this:

```

sudo set | grep -i path

```

My server box yields this output:

```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

So, just stick your script into one of those directories, such as "/usr/local/sbin" (and be sure it's permissions are 0755).

Good luck!

-- Roger

---

### Post by ilrudie on 2008-09-24
Try adding the alias to /etc/bash.bashrc.  Sorry if that was unclear.  

So you make a script somewhere like /opt/bin/myreboot.  Then add an alias like : alias reboot="/opt/bin/myreboot" in either /etc/bash.bashrc for a global change or in ~/.bashrc for just your user.  The change won't happen until you start bash again so run bash or run the alias line manually.

To go back to normal just unalias reboot.

---

