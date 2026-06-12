---
title: "Joining Samba 3 with Active Directory"
date: 2015-02-12
forum: Server Platforms
---

### Post by gardenair on 2015-02-12
hi,
          I am Joining Samba 3 on with my  Active Directory server using Ubuntu .In various tutorials samba with AD joining i  see in  smb.conf file 
 
```
idmap uid = 10000-500000
idmap gid = 10000-500000

```

In each tutorial these values are different. The thing is from where I may get these values ? Is these are predefined what is idmap ? and why these value start from **10000 to 500000**  in some tutorials these values start from **600 to 30000** ......? So it is confusing me ......

My 2nd question is  in global section under 

 ```
----------------------- Standalone Server Options -------------

**    security = users**
[B]    passdb backend = tdbsam

------------------------------------------------------------------
[/B]
```

```
As well under 
----------------------- Domain Members Options ------------------------
**security = users**
[B]    passdb backend = tdbsam
[/B]-----------------------------------------------------------------------------

```

well in my smb.con i change 

```
security = ADS 
```

What is security= ADS ? and in "Standalone Server Options" and in "Domain Members Options" this repeat ** . ***_I want to authenticate samba with windows 2008 so which one should I choose ?_*


My 3rd question is regarding to these following  file

```
**passdb backend = tdbsam**
```

what this line define ? 

please guide me these for these three questions.

thanks
gardenair

---

### Post by lingpanda on 2015-02-13
> **gardenair said:**
> hi,
          I am Joining Samba 3 on with my  Active Directory server using Ubuntu .In various tutorials samba with AD joining i  see in  smb.conf file 
 
```
idmap uid = 10000-500000
idmap gid = 10000-500000

```

In each tutorial these values are different. The thing is from where I may get these values ? Is these are predefined what is idmap ? and why these value start from **10000 to 500000**  in some tutorials these values start from **600 to 30000** ......? So it is confusing me ......

My 2nd question is  in global section under 

 ```
----------------------- Standalone Server Options -------------

**    security = users**
[B]    passdb backend = tdbsam

------------------------------------------------------------------
[/B]
```

```
As well under 
----------------------- Domain Members Options ------------------------
**security = users**
[B]    passdb backend = tdbsam
[/B]-----------------------------------------------------------------------------

```

well in my smb.con i change 

```
security = ADS 
```

What is security= ADS ? and in "Standalone Server Options" and in "Domain Members Options" this repeat ** . ***_I want to authenticate samba with windows 2008 so which one should I choose ?_*


My 3rd question is regarding to these following  file

```
**passdb backend = tdbsam**
```

what this line define ? 

please guide me these for these three questions.

thanks
gardenair

Try following the wiki for Samba [https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server](https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server)

Many of your questions are answered in the link.

---

