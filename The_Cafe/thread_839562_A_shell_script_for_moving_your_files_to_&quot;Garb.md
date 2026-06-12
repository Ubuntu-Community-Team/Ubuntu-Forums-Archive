---
title: "A shell script for moving your files to &quot;Garbage bin&quot;"
date: 2008-06-24
forum: The Cafe
---

### Post by george9233 on 2008-06-24
Hello everyone. I've just written a shell script for moving files to the "Garbage bin". So unlike the "rm" command, you can retrieve files deleted by mistake on the command line simply by opening the garbage bin.

```

#!/bin/bash

until [ "$#" = "0" ];do
    mv $1 "$HOME/.local/share/Trash/files"
    shift
done

```
I saved it as a file named "ga", made it executable and put it in the "bin" folder in my home directory, so after adding "export PATH=$PATH:$HOME/bin" to my .bashrc I was able to use it as a normal command. Certainly it can just be put into "/bin" directory.

Since there's a loop, I'm able to operate on multiple files and/or folders. It's quite useful I think.

---

### Post by kc600 on 2009-10-05
Thanks dude! I took the liberty of improving on it slightly, so the metadata (deleted when, and where from) are also stored: [http://keeshink.blogspot.com/2009/10/shell-script-for-moving-files-to-trash.html](http://keeshink.blogspot.com/2009/10/shell-script-for-moving-files-to-trash.html)

---

### Post by NoaHall on 2009-10-05
It's easy to make.

---

### Post by bigboy_pdb on 2009-10-05
You can simplify your script even more by making it:

```

#!/bin/bash
mv "$@" "$HOME/.local/share/Trash/files"

```

---

### Post by sisco311 on 2009-10-05
hhhm, reinventing the wheel?

```
trash path/to/file
```
```
man trash
```

---

### Post by kc600 on 2009-10-06
@bigboy: this doesn't create the info file.
@sisco: i found the app in the 'trash-cli' package, thanks for pointing this out!

---

### Post by bigboy_pdb on 2009-10-06
> **kc600 said:**
> @bigboy: this doesn't create the info file.

You're right. I had just looked at the first command, noticed it could be simplified, and thought it might be good to give a shorter version. I hadn't even thought about the mechanics of the trash bin or checked the other script. Sorry about that.

Now that you've mentioned it and I've looked at the link for the second version of a trash script and the source for trash-cli and I don't really think it's a good idea to write or use custom scripts to modify the trash bin since the trash applet will change over time and using custom trash scripts can corrupt it. trash-cli doesn't appear to be sharing code with the applet. If it were, I'd feel differently about it.

If a person knows about the location of trash files and how to clear it when it's corrupt then doing that might not be so bad.

---

