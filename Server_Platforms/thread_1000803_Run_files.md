---
title: "Run files"
date: 2008-12-03
forum: Server Platforms
---

### Post by any.linux12 on 2008-12-03
Hi

I need to install a program and I must run nsm_linux_cli_3_20_05.run. The thing is that I already did that in a workstation and now I need to do in the server by ssh but the server doesn't run the file 

> 
root@espSRV01:/home/esp-admin# ./nsm_linux_cli_3_20_05.run 
bash: ./nsm_linux_cli_3_20_05.run: No such file or directory


is there any application needed to run that file?? Because the server is new and I don't know if is any plication missing.

---

### Post by cdenley on 2008-12-03
> **any.linux12 said:**
> Hi

I need to install a program and I must run nsm_linux_cli_3_20_05.run. The thing is that I already did that in a workstation and now I need to do in the server by ssh but the server doesn't run the file 



is there any application needed to run that file?? Because the server is new and I don't know if is any plication missing.
Are you sure the file is there and executable by your user?
```

whoami
ls -l nsm_linux_cli_3_20_05.run
chmod +x nsm_linux_cli_3_20_05.run

```
Are you sure you can trust that executable?

---

### Post by any.linux12 on 2008-12-03
The file was already in mod 755 and I already did this in a machine.
Now I'm trying by ssh and I can't do it

---

### Post by ibutho on 2008-12-03
Are you sure you are entering the correct filename and that you are working in the directory where the file is located?

---

### Post by cdenley on 2008-12-03
> **any.linux12 said:**
> The file was already in mod 755 and I already did this in a machine.
Now I'm trying by ssh and I can't do it

Well, judging from the error, I don't think the file exists where you are trying to execute it from.

POST THIS OUTPUT
```

file nsm_linux_cli_3_20_05.run
ls -l nsm_linux_cli_3_20_05.run
./nsm_linux_cli_3_20_05.run

```

And once again, run the file at your own risk. Running executables like this is not recommended.

---

### Post by Krupski on 2008-12-03
> **any.linux12 said:**
> The file was already in mod 755 and I already did this in a machine.
Now I'm trying by ssh and I can't do it

Does it say "command not found" when you try to run it?

You may be trying to run a 32 bit program in 64 bit Linux.

To do so, you need the 32 bit libraries.

Go to the root directory of your server and see if there's a directory called "lib" and a symlink called "lib64" pointing to it. If so, you have a 64 bit installation. Then look to see if you ALSO have a directory called "lib32". If not, you need to install the 32 bit libraries.

Get them like this:

```

sudo apt-get -V install ia32-libs

```

Good luck (and be sure of what that .run executable is before you run it).

-- Roger

---

### Post by hictio on 2008-12-03
Another shot...
Have you paged thru the file? (Using less or similar)
Perhaps it is referencing an interpreter that you don't have installed, or that you have installed on a different path than the one on the file?

Example:

```

#!/usr/local/bin/bash

```

---

