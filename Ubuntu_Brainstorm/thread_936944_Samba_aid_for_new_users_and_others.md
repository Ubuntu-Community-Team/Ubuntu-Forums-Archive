---
title: "Samba aid for new users and others"
date: 2008-10-03
forum: Ubuntu Brainstorm
---

### Post by ubuntu1sttimer on 2008-10-03
Back on Dapper I was finally able to get SAMBA working for drive sharing. Then Dapper locked up and I had to reinstall. That was almost a year ago and still have not been able to get SAMBA working again. My setup is not the simplest and I have not found the combination. 

This is not a request for help but rather in response to all the other requests for aid in getting SAMBA going on Ubuntu. There are reams of help files with ideas on how to do Samba but there are still many messages on these boards from those that are having problems.

With that in mind, how about someone(s) preparing some smb.conf configuration files for SAMBA that are built for different applications. Lots of remark entries to guide new users on what changes can be made to a configuration line to support different needs. 

Or better yet, a question and answer script that builds a SMB.CONF file based on what they say they need. SWAT is good but if you are not a SAMBA expert, it does not provide much help getting you get up and running.

This would be aimed at those who are not power users but rather people who would like to leave Windows but need to have file/drive sharing. 

For those that are inclined to say that SAMBA is easy to set up, compare it to what is involved in doing a drive share in Windows.

UBUNTU is a powerful and versatable operating system but for most users, the kind of difficulties involved in getting SAMBA going is enough to get them to give up LINUX for life and send them to back to the "WINDOWS store".

---

### Post by cdenley on 2008-10-03
> **ubuntu1sttimer said:**
> Back on Dapper I was finally able to get SAMBA working for drive sharing. Then Dapper locked up and I had to reinstall. That was almost a year ago and still have not been able to get SAMBA working again. My setup is not the simplest and I have not found the combination. 

This is not a request for help but rather in response to all the other requests for aid in getting SAMBA going on Ubuntu. There are reams of help files with ideas on how to do Samba but there are still many messages on these boards from those that are having problems.

With that in mind, how about someone(s) preparing some smb.conf configuration files for SAMBA that are built for different applications. Lots of remark entries to guide new users on what changes can be made to a configuration line to support different needs. 

Or better yet, a question and answer script that builds a SMB.CONF file based on what they say they need. SWAT is good but if you are not a SAMBA expert, it does not provide much help getting you get up and running.

This would be aimed at those who are not power users but rather people who would like to leave Windows but need to have file/drive sharing. 

For those that are inclined to say that SAMBA is easy to set up, compare it to what is involved in doing a drive share in Windows.

UBUNTU is a powerful and versatable operating system but for most users, the kind of difficulties involved in getting SAMBA going is enough to get them to give up LINUX for life and send them to back to the "WINDOWS store".

-install samba
-right click directory, select properties
-select "Share" tab
-choose whatever options
-click "Create Share"

Seems simple enough.

---

### Post by olskar on 2008-10-03
> **cdenley said:**
> -install samba
-right click directory, select properties
-select "Share" tab
-choose whatever options
-click "Create Share"

Seems simple enough.

You don't even have to install samba first, its automatically done when trying to share a folder (if it is not installed) :)

But something that might be a bit confusing is that you have to logout before this will work after you have installed samba..and you are not told to do that..perhaps that is something that could be improved?

---

