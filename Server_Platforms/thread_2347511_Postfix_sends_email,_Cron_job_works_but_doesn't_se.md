---
title: "Postfix sends email, Cron job works but doesn't send completion email notification"
date: 2016-12-26
forum: Server Platforms
---

### Post by agarwaldvk on 2016-12-26
Hi Everyone


I recently installed Postfix. I have also tested that it works by manually sending an email to myself to my Gmail account using the following command at the terminal :-

echo "test" |  mail -s "Subject MyTest_20161226_1942" [email]emailaddress[/email]

I have also set up a cron job to run a script file like so :-

The script file path and name is '/home/agarwaldvk/test.sh'

The file contents are like so :-

```

#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
#echo "$mytext $todaysdatetime" >> /home/agarwaldvk/testoutput.txt

```

I have tested it and it runs Ok. The cron job just writes the current date in a file called 'testoutput.txt' which is located at '/home/agarwaldvk/' location

The output file contents when the cron job was last run is reproduced below :-

the program has been run at : Monday 26 December  11:18:01 AEDT 2016
the program has been run at : Monday 26 December  11:20:01 AEDT 2016
the program has been run at : Monday 26 December  11:22:01 AEDT 2016


The cron job, however, doesn't send me an email notification of its successful completion or failure. I was hoping to be able to set i[ the cron job to do just that, that is, send me an email whether or not the cron job was successfully completed or has failed tp complete the case might have been.

Is there a way to tell the cron job to send me an email status report of the job - both failure and success?

This is in preparation of the cron job that I am intending to create to schedule my backups - I am intending to use 'Backup2l' to do so - I haven't implemented it yet but I was hoping to try that out once I got my cron job and email things set up. So, if someone can help me fix up the email notifications of my cron jobs, I can then start looking at implementing my scheduled backup jobs.


Best regards


Deepak

---

### Post by SeijiSensei on 2016-12-26
You could add a line to the end of the script like this:
```

mail -s 'Cron job successful' you@example.com

```

---

### Post by bearlake on 2016-12-26
@ agarwaldvk, if thats your real email address, delete it before you get spam to death by bots.[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=71528")

---

### Post by agarwaldvk on 2016-12-27
Hi bearlake


Thanks for your response but where do I remove this email from?

The script file doesn't have any email addresses specified. The cron job only runs the script file at the predefined intervals.

I was doing some reading and was about to consider doing this :-

redirect the entire output of the command (both the standard output and the error output if there were to be any) like so :-

```

#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
echo "$mytext $todaysdatetime" >> /home/agarwaldvk/testoutput.txt 2>&1

```


to a text (or log) file as shown above.

And then change the script file like so that the new script file will look something like as shown below to have have the contents of the text (or log) file sent to me at the completion of the cron job :-


```

#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
echo "$mytext $todaysdatetime" >> /home/agarwaldvk/testoutput.txt 2>&1 mail -s "Cron job status report" < /home/agarwaldvk/testoutput.txt             #assuming that the output has been redirected to the text file 'testoutput.txt'

```

Would this be a problem?

As I had mentioned earlier, this is in the context of having the status report of the backup job (to be implemented as a cron job using 'backup2l') to be sent to me at the completion (or failure) of the job.


Edit:-
Just ran the cron job and it worked OK except that it did not send out any emails to me with the contents of the file. Shouldn't it have to the root user (sudo privileged user 'agarwaldvk' in this case) without having to specify the user in 'mail' part of the command?


Best regards


Deepak

---

### Post by SeijiSensei on 2016-12-28
> **agarwaldvk said:**
> Hi bearlake
Thanks for your response but where do I remove this email from?
I believe he or she meant to remove it from your posting here.

> 
```

#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
echo "$mytext $todaysdatetime" >> /home/agarwaldvk/testoutput.txt 2>&1 mail -s "Cron job status report" < /home/agarwaldvk/testoutput.txt             #assuming that the output has been redirected to the text file 'testoutput.txt'

```


That final line has bad syntax.  The mail command needs to be on a separate line:
```

#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
echo "$mytext $todaysdatetime" >> /home/agarwaldvk/testoutput.txt 2>&1 
mail -s "Cron job status report" < /home/agarwaldvk/testoutput.txt

```

The use of ">>" means that the output of each invocation of this script will be appended to testoutput.txt.  Do you really want to see all the output repeated over and over again?  If not, just use ">" which will recreate testoutput.txt from scratch each time the script is executed.

---

### Post by agarwaldvk on 2016-12-28
Hi  SeijiSensei


Thanks for your comments.

I will go through the post and remove the email if I have included my real email therein. Didn't realize that!

I have corrected the >> to > to make sure that the file is empty before each run and also that mail appears on a separate line in the script file.

Edit :-
Just checked - there is no mention of my real email address in the entire posting!



Best regards


Deepak

---

### Post by SeijiSensei on 2016-12-28
> **agarwaldvk said:**
> Just checked - there is no mention of my real email address in the entire posting!
I didn't see one either.

---

### Post by bearlake on 2016-12-28
> **agarwaldvk said:**
> Hi bearlake


Thanks for your response but where do I remove this email from?

The script file doesn't have any email addresses specified. The cron job only runs the script file at the predefined intervals.

I was doing some reading and was about to consider doing this :-

redirect the entire output of the command (both the standard output and the error output if there were to be any) like so :-

```

#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
echo "$mytext $todaysdatetime" >> /home/agarwaldvk/testoutput.txt 2>&1

```


to a text (or log) file as shown above.

And then change the script file like so that the new script file will look something like as shown below to have have the contents of the text (or log) file sent to me at the completion of the cron job :-


```

#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
echo "$mytext $todaysdatetime" >> /home/agarwaldvk/testoutput.txt 2>&1 mail -s "Cron job status report" < /home/agarwaldvk/testoutput.txt             #assuming that the output has been redirected to the text file 'testoutput.txt'

```

Would this be a problem?

As I had mentioned earlier, this is in the context of having the status report of the backup job (to be implemented as a cron job using 'backup2l') to be sent to me at the completion (or failure) of the job.


Edit:-
Just ran the cron job and it worked OK except that it did not send out any emails to me with the contents of the file. Shouldn't it have to the root user (sudo privileged user 'agarwaldvk' in this case) without having to specify the user in 'mail' part of the command?


Best regards


Deepak

Hi,

Read the fine print on the bottom of your 1st post.

One of the mods removed your email address for you. 

All is good. :)

---

