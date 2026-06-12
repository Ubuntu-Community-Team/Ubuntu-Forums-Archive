---
title: "Checking if users exist"
date: 2011-06-28
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-06-28
hi guys.
Not sure if this is the right place fo this but....

I'm just learning to write bash scripts. I'm experimenting on a ubuntu server 11.04 virtual machine.

As part of the script I want to automate user creation.

Is there a way to check if a user already exists in a script. so i can do something like

```
if userexists; then
do this
else
do this instead
fi

```

---

### Post by papibe on 2011-06-28
There's no simple command to do that (at least that I know). You have to search the /etc/passwd file. This is part of a working code that I have used in the past:
```
#!/bin/bash

UserExist()
{
   awk -F":" '{ print $1 }' /etc/passwd | grep -x $1 > /dev/null
   return $?
}


UserExist $1
if [ $? = 0 ]; then
   echo "$1 exists."
else
   echo "$1 does not exist."
fi
```

To test it, run it like this:
```
$ ./the_above_script.sh   name_of_user_you_want_to_test
```
Hope it helps.

---

### Post by samosamo on 2011-06-28
Don't depend on /etc/passwd. nsswitch.conf is capable of using multiple databases. You should use "getent passwd" in Linux to query this information.

This was not tested but here is the idea:

```
#!/bin/bash

if [ -z $(getent passwd jsmith) ]
then
 echo user exists

else
 echo user does not exist

fi
```

---

### Post by papibe on 2011-06-28
Thanks, good to know. BTW, I took the liberty of making some corrections to your script. This works on my system:
```
#!/bin/bash

if [ -z "$(getent passwd jsmith)" ]; then
    echo "user does NOT exist."
else
    echo "user DOES exist."
fi

```

---

### Post by rubylaser on 2011-06-28
That is good to know.  I've always used /etc/passwd for this.  Thank you for sharing :)

---

### Post by bigmonmulgrew on 2011-06-29
Well thanks for thats guys.
I will test that on my system shortly

---

### Post by bigmonmulgrew on 2011-06-29
Hi guys just thought I'd post my results for you

Heres what I finally went with
```

function get_user
{
echo -n "Enter a new user name > "
read username
echo "You entered: $username"

if [ -z "$(getent passwd $username)" ]; then
        echo "User name does not exist and will be created."
else
        echo "This username is already taken or is invalid."
        echo "Please try a different user name"
        get_user
fi
}

```
I'm sure this is a fairly common use. I've simply set it to ask for the username again if the previous one is taken.
I suppose I could add conditions here to invalidate it for other reasons like min or max string or even if it contained offensive words or invalid characters. I dont really have a need for this at the moment and I'm not sure how to do it so I'm going to move on for new.


here is the output of the script (or the user bit anyway.)
```
Before operations begin some user data is needed
Enter a new user name > admin1
You entered: admin1
This username is already taken or is invalid.
Please try a different user name
Enter a new user name > adminz
You entered: adminz
User name does not exist and will be created.
Enter a new password >
...
...
```

---

