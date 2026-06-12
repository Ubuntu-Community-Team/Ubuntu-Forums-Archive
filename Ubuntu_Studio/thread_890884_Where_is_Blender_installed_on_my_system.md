---
title: "Where is Blender installed on my system"
date: 2008-08-15
forum: Ubuntu Studio
---

### Post by jadhav333 on 2008-08-15
I have Ubuntu 8.04 on my quad-core Box.

I installed Blender 2.45 through the "Add/Remove Applications" feature of Ubuntu.

I now have a compressed file of a (Blendigo) plugin for blender. The instructions are to copy the different contents of the compressed file at different locations within the blender installed folder.

I really dont know where all the Blender installed files are. Can u help me find the same?

Thanks

---

### Post by Stochastic on 2008-08-15
Blender files are placed in various locations on your hard drive.  To find all file paths that include the word 'blender' do ```
locate blender
```

/usr/bin/blender is the location of the executable file, but when I execute the above command, there are a large number of folders with blender files.

Another useful technique is to pipe the output of that command to grep (this is done with the | character), and grep will filter the results by whatever word you choose.  Try ```
locate blender | grep plugins
```
That command gives the folder I would try first when installing blender plugins.

---

### Post by jadhav333 on 2008-08-15
Thanks Stochastic..

This worked.. now i know where the folders are located..

But while I try to copy the plugin files to repective folders,,i get permission  denied error.. for eg.. in the /usr/share/blender/scripts folder..

Pls advise..

---

### Post by Stochastic on 2008-08-16
You can use sudo to make yourself look like the root user (admin account) so that you can write in the write protected folders.  But I'd be careful about making sure all your permissions on any copied files have the appropriate permissions (check this with "ls -l" and do any corrections with chmod).

You should take a look at the instructions for all these commands when you have time (probably at least look at the chmod command's instructions before using it).  You can read their instructions (i.e. manual) by doing ```
man chmod
```

---

