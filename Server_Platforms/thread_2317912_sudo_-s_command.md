---
title: "sudo -s command"
date: 2016-03-21
forum: Server Platforms
---

### Post by amitha3 on 2016-03-21
Hi,

I wanted to stop the password prompt when a script is running. I used **sudo -s** inside my script. But now when I exit from the script sudo doesn't prompt for the password at all. How do I get it back since that is dangerous, since I executed it inside one of my servers (ubuntu 14.04) ?

Thanks :)

---

### Post by oldfred on 2016-03-21
More info on sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But it was my understanding that you never use sudo in a script. You run script with sudo bash.
My first script was several commands copied from my history & I edited out all the sudo, and added bash header & script worked.

---

### Post by MAFoElffen on 2016-03-24
The default "time" that sudo lingers after it is used is 5 minutes. That is varied by a policy. Using sudo with a "-v" option adds another 5 minutes to that. But you say it is going longer? Or that you don't want it at all when the script completes?

Just thinking out the logic of what you said...

If you use "-c", instead of "-s" as an option, you elevate for that command. If you use an "-s" option, you actually load an instance of a shell. If you use that alone without a command after it, remember to throw in an "exit" to dispose of that shell instance, or it stays loaded. Doing that should dump the sudo lingering for that shell instance, right?

---

### Post by amitha3 on 2016-03-25
Hi All,

Thank you for your valuable information. Will get back to you after going through these links

Thanks again

Amitha:)

---

### Post by amitha3 on 2016-03-25
Hi All,

Now when I use **sudo** before a command it prompts for the user's password. I think after the server has been restarted it behaves the earlier way. Problem is ok now.

Thank you all for your great help.....!!! I learned a lot from referring your information.

Thanks :):):)

---

### Post by MAFoElffen on 2016-03-27
You are welcome. Happy that it works for you now.

Please revisit this thread > Go to the link to the top right of the first post that says "Thread Tools" > Select "Mark as Solved."

This will help others with the same question to be able to find answers to their similar questions.

---

