---
title: "How can I retrieve Active Directory users' primary group in Ubuntu?"
date: 2010-02-20
forum: Server Platforms
---

### Post by jaimerosario on 2010-02-20
This is the scenario:

Active Directory Server = 192.168.0.1
Squid/Dansguardian Proxy Server w/NTLM Auth = 192.168.0.10

The Linux box has been integrated with AD and works fine. Users can authenticate automatically when login the AD or when they access the web through Basic authentication. That part is just fine.

But, when I add a new user, or change a users' primary group, I have to change the 'filtergroups' file in Dansguardian.

I tried to make auto this process using the USERMAP and USERMAP2 scripts in [http://www.dansguardian.org](http://www.dansguardian.org) at the "Extras and Add Ons" section, but both scripts doesn't run properly in Ubuntu if they are not changed. I tried, following the instructions, but got a lot of syntax errors...

So, I wrote a very simple script using 'net rpc' to retrieve all users according to the AD Security and Domain Groups.

I created an output folder in dansguardian to dump the rpc outputs into files. And read the files to apply filtering groups.

The script is the following:


rm /etc/dansguardian/grouplist/*;
/etc/dansguardian/grouplist/group0A;
net rpc group MEMBERS Administrators -I192.168.0.10 -Uadministrator%password$ | cut -c6-99 | awk '{print $0"=filter4"}' > /etc/dansguardian/grouplist/group0B;
net rpc group MEMBERS Teachers -I192.168.0.10 -Uadministrator%password$ | cut -c6-99 | awk '{print $0"=filter3"}' > /etc/dansguardian/grouplist/group1B;
/group2A;
net rpc group MEMBERS Students -I192.168.0.10 -Uadministrator%password$ | cut -c6-99 | awk '{print $0"=filter2"}' > /etc/dansguardian/grouplist/group2B;
cd /etc/dansguardian/grouplist;
cat group* > filtergroupslist;
mv /etc/dansguardian/lists/filtergroupslist /etc/dansguardian/lists/filtergroupslist.old;
cp /etc/dansguardian/grouplist/filtergroupslist /etc/dansguardian/lists/filtergroupslist;
/etc/init.d/dansguardian restart;

As I wrote before, the script does what I need automatically. But As a result, I'm getting duplicated users in different and inferior filtering groups.

What I want to do is to erase duplicated users that applied for a inferior filtergroup.

for example: If the script outputs user "Happy_Monkey" is a member of Domain Users and Domain Admins, then in 'filtergrouplist' "Happy_Monkey" will be found like:

Happy_Monkey=filter4 # filter4 is for Administrators
Happy_Monkey=filter3 # filter 3 is for Users

All I want is to delete the inferior "Happy_Monkey" line, and that will be "Happy_Monkey=filter3", leaving "Happy_Monkey=filter4" on filtergrouplist

I don't want others to make it for free, however, it will be welcome. I just need to be pointed into the right direction.

I'm new into scripting. Still I don't understand those "if-do-while-case-shift-for-then" things on scripting.

Any help, pointing me into the right direction, or explaining me some process will be welcome.

---

### Post by HermanAB on 2010-02-20
Howdy,

Using Samba Winbind, you can investigate the domain records with:

# wbinfo -u 
# wbinfo -g 
# getent password 
# getent group

---

### Post by jaimerosario on 2010-02-20
What I'm trying to do is that if there is a way to get the primary group of the user via "net ads", "net rpc" or so, to integrate it into the script I made.

I need some command or combination of commands that outputs the user primary group only.

If user "Happy_Monkey" is part of:

Administrators (primary group)
Domain Admins
Domain Users
Users

I want a command or script that tells me only the primary group, so I can have the following output (or sort of):

Happy_Monkey=Administrators

All the winbind and samba commands I've tried only tell me all the groups the user is member of.

If is not possible, then a script or processes that I can erase automatically duplicated users with inferior filtergroups in '/etc/dansguardian/lists/filtergrouplist'

I appreciate your help. I tried, but is already what I have right now.

---

### Post by koenn on 2010-02-20
The Primary Group is an Ugly Workaround (TM) bij Microsoft to circumvent a 5000 member hard limit for  members per group. This workaround makes it pretty hard to retrieve this information. 
see:
[http://support.microsoft.com/default.aspx?scid=kb;en-us;321360](http://support.microsoft.com/default.aspx?scid=kb;en-us;321360)
[http://support.microsoft.com/default.aspx?scid=kb;en-us;297951](http://support.microsoft.com/default.aspx?scid=kb;en-us;297951)


In your case, you  could probably insert an additional filter in the pipelines of your script, 
eg (peudo code)
```
get group members Teachers | grep username Administratorlist || ( echo username >> teacherfilterlist )
```

' || ' means 'OR', so either grep finds 'username' in 'administratorlist' (and nothing else happens), OR userrname will be added to the teacherlist

note that this will only work if you query the groups in the right order, Aminst first, then teachers, then users, as you're doying now.


An alternative way would be to not just cat all the files together, but compare them in a specific order and remove duplicates before or while creating the final list.

A 3rd option might be to just make the final list, duplicate usernames and all, sort it, then check for matches or duplicates on the first X chars of each line, and remove all matching (partially) duplicate lines. X would have to be a number of chars small enough to exclude the filter=3, filter=4 portions of the lines.

---

