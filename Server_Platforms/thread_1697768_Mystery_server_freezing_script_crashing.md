---
title: "Mystery server freezing script crashing"
date: 2011-03-01
forum: Server Platforms
---

### Post by kaspar_silas on 2011-03-01
Hi hopefully someone can help with a strange little issue 
I discovered in running a script on a remote server. 

Take this little demonstration script:

```

#!/bin/bash
exec 6>&1 #Link file descriptor 6 to standard stdout
exec > /dev/null #redirect stdout 
echo "Nothing"
exec 1>&6 6>&- #restore stdout and delete file descriptor

```

This runs as expected (it does nothing) on both my local desktop and the remote server. However if I log in via ssh to the remote server and run this script everything on the server freezes. I do mean everything ftp/ssh/nfs/login-requests/... even if I go and physically plug in monitor and keyboard there is no response. It basically needs a full restart to clear. 

I have repeated this several times. Now something is clearly wrong here but does anyone know what. I didn't think a non-admin user should be able to actually lock up system processes.

Any ideas? O and if any brave people test it on their servers do let me know how that goes.

The system is dell power edge server running 64b 9.10.

---

### Post by kaspar_silas on 2011-03-03
M, okay. Well can someone else confirm the problem. It's 5 for 5 at my side.

---

### Post by kaspar_silas on 2011-03-07
Really?

---

