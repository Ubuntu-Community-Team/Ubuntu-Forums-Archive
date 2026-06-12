---
title: "Multi threading?"
date: 2011-03-12
forum: Server Platforms
---

### Post by ubbrown88 on 2011-03-12
Following from this thread [http://ubuntuforums.org/showthread.php?p=10551505](http://ubuntuforums.org/showthread.php?p=10551505)

The command

whois google.com
shows the info about google.com
and so on

I have a pretty big list of domains right now with me and I want to do a whois for all of these domains and save the results.

Since file is big, I will need multi processing.

Is it possible to implement multithreading/multi processing into it?

Like doing whois of say 3 or 4 domains at the same time?

I am thinking that I might use it for finding available and domain researching as well! This is just so wonderful, people charge money for it and we can do it for all free with Ubuntu.

---

### Post by ubbrown88 on 2011-03-14
No one knows?

---

### Post by BkkBonanza on 2011-03-14
Well to do actual multi-threading it would have to be written in the program but what you actually mean is multiple concurrent processes - and that is easy.

You just need to make a smarter script that starts each lookup as a background process. You would need to pipe the output into a different file for each process or else they would stomp on each other's output. You also would want to put the onput lists in seperate files or feed them into each sub-process from the script (via stdin).

At the end you could wait for tasks to end and combine the output files into one. That gets a bit fancy though as you need to save and monitor the pids. Otherwise it's pretty straightforward. 

There are multi-threaded gui tools I've seen for who is lookup for doing batches. I don't recall the name now as it was long ago.

I'm not aware of anyone charging money for whois lookup but if they are then what a scam since it's free from most domain resellers. Some domain resellers have pretty nice domain searching too. I use the one at **name.com** and it's pretty thorough at finding name combos and various TLDs.

---- 

This example puts each domain in it's own txt file. Paste this into a file called **manywhois** and **chmod 700 manywhois** so it can be exec'd. Run it by typing ./manywhois at the command prompt (assuming same directory - if you copy the file to /usr/local/bin then it should be in the path and can be run without the ./ in front but also then you would want to code in a path for the output files).

```

#!/bin/bash

while read X;
do
whois $X > $X.txt&
done <test.txt

```

Note the & after the whois command - that starts the whois as a background task which detaches from the script and keeps running while the script continues to the next domain name. 

This starts a new process for each domain and if you want to limit how many then you'd need some extra code to watch how many are running and wait for one to end before starting a new one. If you hit some limit of the whois server then you'll likely get errors back instead of data.

Warning: I suspect if you pound on the networksolutions (or other) whois service too hard they may temporarily black list you. I don't know what their restrictions are but typically hitting something like this hard is viewed as abusive.

---

### Post by ubbrown88 on 2011-03-14
> **BkkBonanza said:**
> Well to do actual multi-threading it would have to be written in the program but what you actually mean is multiple concurrent processes - and that is easy.

You just need to make a smarter script that starts each lookup as a background process. You would need to pipe the output into a different file for each process or else they would stomp on each other's output. You also would want to put the onput lists in seperate files or feed them into each sub-process from the script (via stdin).

At the end you could wait for tasks to end and combine the output files into one. That gets a bit fancy though as you need to save and monitor the pids. Otherwise it's pretty straightforward. Just ask if you need an exmaple.

There are multi-threaded gui tools I've seen for who is lookup for doing batches. I don't recall the name now as it was long ago.

I'm not aware of anyone charging money for whois lookup but if they are then what a scam since it's free from most domain resellers. Some domain resellers have pretty nice domain searching too. I use the one at **name.com** and it's pretty thorough at finding name combos and various TLDs.

Thanks, I checked the name.com and it looks quite good. Better than internetbs.net which I am using right now.

Can you please tell me the steps or exact code for doing this? I am really new to the ubuntu and doesnt know much about it.

Thanks again

---

### Post by BkkBonanza on 2011-03-14
I edited the post above to have an example. 
But you were too quick to see it :)

Edit: just re-edited it as well as the first version wouldn't work as a single line command. I put it in a script file and it worked fine.

---

### Post by ubbrown88 on 2011-03-14
> **BkkBonanza said:**
> I edited the post above to have an example. 
But you were too quick to see it :)


Thanks

It gives me error saying "bash: syntax error near unexpected token `**;**'

---

### Post by BkkBonanza on 2011-03-14
Ya, doesn't work as is from prompt. I updated it to be a script see above again. There's probably some syntax to just run it at the prompt but it doesn't pop into my head right now.

---

