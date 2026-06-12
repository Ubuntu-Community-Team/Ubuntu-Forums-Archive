---
title: "Valid characters for useradd command"
date: 2015-12-07
forum: Server Platforms
---

### Post by gardenair on 2015-12-07
hi,
     I want to know that for Linux system to add a new user can we use "." , "_"  and "-" these are** dot,underscore,hyphen** ?
Example 

```
[B]# useradd user1.test
# useradd user2_test
# useradd user3-test[/B]
```

Are these three characters are valid during adding a new user name ?

2- Now 2nd query is after creating my users I create a new group 

```
# groupadd IT
```

 want to add these users into group "IT"

```
# usermod –a  G  IT user1.test
```

It added successfully added. There is also a switch " -g " what is the main difference between " G " and "-g"


Thanks

---

### Post by matt_symes on 2015-12-07
Hi

From

```
man useradd
```

> There is also a switch " -g " what is the main difference between " G " and "-g"

```

       -g, --gid GROUP                                                                                                        
           The group name or number of the user's initial login group. The group name must exist. A group number must         
           refer to an already existing group.                                                                                
                                                                                                                              
           If not specified, the behavior of useradd will depend on the USERGROUPS_ENAB variable in /etc/login.defs. If       
           this variable is set to yes (or -U/--user-group is specified on the command line), a group will be created for     
           the user, with the same name as her loginname. If the variable is set to no (or -N/--no-user-group is specified    
           on the command line), useradd will set the primary group of the new user to the value specified by the GROUP       
           variable in /etc/default/useradd, or 100 by 
default.                                                               
                                                                                                                              
       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]                                                                             
           A list of supplementary groups which the user is also a member of. Each group is separated from the next by a      
           comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with     
           the -g option. The default is for the user to belong only to the initial group.  
```

You'll need the -G switch for what you are trying to do.

> Are these three characters are valid during adding a new user name ?
```

It is usually recommended to only use usernames that begin with a lower case letter or an underscore, followed by      
       lower case letters, digits, underscores, or dashes. They can end with a dollar sign. In regular expression terms:      
       [a-z_][a-z0-9_-]*[$]?                                                                                                  
                                                                                                                              
       On Debian, the only constraints are that usernames must neither start with a dash ('-') nor plus ('+') nor tilde       
       ('~') nor contain a colon (':'), a comma (','), or a whitespace (space: ' ', end of line: '\n', tabulation: '\t',      
       etc.). Note that using a slash ('/') may break the default algorithm for the definition of the user's home             
       directory.                                                                                                             
                                                                                                                              
       Usernames may only be up to 32 characters long. 
```

Kind regards

---

### Post by darkod on 2015-12-07
Also just to point out that you can't leave space between the a and the G in usermod, unless you use -G instead of only G.

The command is:
```
usermod -aG IT <username>
```
or
```
usermod -a -G IT <username>
```

---

