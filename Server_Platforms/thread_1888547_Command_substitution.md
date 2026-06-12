---
title: "Command substitution"
date: 2011-11-29
forum: Server Platforms
---

### Post by vsiege on 2011-11-29
```
instanceId=`wget -q -O - http://169.254.169.254/latest/meta-data/instance-id`
    echo $instanceId
    reset=$(sudo ec2-describe-tags   --filter \"resource-id=${instanceId}\" --filter \"key=reset\" | cut -f5)
```
Issue:    
The command substitution i'm trying to do **{instanceId}** with reset is what is failing. I can't seem to get the variable instanceId to work correctly. 

As I know i have no typo's, how do you successfully substitute a system variable in a command line?

---

### Post by papibe on 2011-12-05
Could you give us a little more information?

What is the result you want to get?
What are the results you are getting now?

Regards.

BTW, I would not put a 'sudo' inside a script, but call the script using sudo. Just a thought.

---

### Post by aeiah on 2011-12-06
have you tried removing the curly brackets from the variable?

```

ec2-describe-tags   --filter \"resource-id=$instanceId\" --filter \"key=reset\" | cut -f5

```

&yea, i agree, take out the sudo from the script and run the script as root if need be. no point having to enter the password halfway through

---

