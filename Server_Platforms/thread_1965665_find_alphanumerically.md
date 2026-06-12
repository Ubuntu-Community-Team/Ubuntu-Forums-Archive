---
title: "find alphanumerically"
date: 2012-04-26
forum: Server Platforms
---

### Post by Valpskott on 2012-04-26
I have a server setup to render videos using 2 scripts. The first script checks a folder for subfolders(containing the video files) which to process and render using a second script. Now, everything is working just fine, except for a minor detail.

The order in which the subfolders are being processed are not alphanumerical. The videos are episodic in nature, and sometimes I'm in a hurry to upload the next episode, so it would be great if the script could render the subfolders in alphanumerical order, instead of just grabbing subfolders at random until every subfolder have been processed.

This is the first script:
```
#!/bin/bash

find /home/johan/Video/Custom/ -mindepth 1 -depth -type d -print0 | xargs -r0 /home/johan/Video/Script-B.sh
```

Now, I got help with the first script when I first made it, so in all honesty, I do not understand the syntax well enough to start fiddling with it.

I've checked both the man page for xargs and find, and it seems like none of them have a flag for alphanumerical sorting.

Is it possible to pipe it into the sort command if "find" itself doesn't have a flag for alphanumerical ordering, and how do I do this? (I'm new to piping things) Just insert "sort | " before "xargs"?

Like this
```

find /home/johan/Video/Custom/ -mindepth 1 -depth -type d -print0 | sort | xargs -r0 /home/johan/Video/Script-B.sh
```

---

### Post by papibe on 2012-04-26
Hi Valpskott.

It all depends on your directory structure. If there is not subdirectories, that may just work (although you need to use sort with -z option for null terminated strings).

If you have a tree structure, some extra work would be needed. Since find returns the whole path of the file, 'sort' would fail to sort correctly when episodes of the same show are in different directories.

I hope that helps, and tell us if you need more help with that.
Regards.

---

### Post by Valpskott on 2012-05-03
Hello Papibe!

First, thank you for your answer.

I just ran the "sort -z" pipe after the find command and outputted it into a txt file, and it looks like it will work. I'll try the real deal the next time I have some acctual episodes to process. Thanks :D

---

