---
title: "Looking for Specific Open source solution"
date: 2008-07-30
forum: The Cafe
---

### Post by Proto_ on 2008-07-30
I am not sure if this is in the right place, but i need help

I work for a consulting company and we have consultants spread all over the world, thus making backup and project transfer a nightmare.
The company is small, thus, i have very limited resources, which is the reason why i am running ubuntu on the two servers we have.

Many of our consultants cannot use FTP or even browse the web, being stuck to an email-only communication with the outer world.

What i am looking for is a solution (or group of solutions, or some way in which i can write something (i know a bit of PHP and Python), or any help at all) that can:

[LIST]
[*]receive emails every 10 minutes
[*]store those email attachments in separate folders, depending on the email sender and subject
[*]on request, verify a user's password and send it a list of all the files he has ever stored, separated by project
[*]upon request, send someone a specific file, all his files or all files related to a specific project
[/LIST]

I know it seems kind of stupid, but it may work. I am willing to collaborate in any way i can with anyone to make this happen and then give the project back to the community.

Thank you very much to all.

---

### Post by freebeer on 2008-07-30
Have you looked into Zimbra (for the back-end) and Zimbra Desktop for the clients?  It might do what you're looking for.

---

### Post by Proto_ on 2008-07-30
Thanks! Will look at it tomorrow.

But, from your answer, I find that I may not have made myself clear enough.

There can be no client or frontend. All the information has to be transferred by e-mail. Some use cases below:

**Use case 1:**
Bob send an email with a report.doc attached and the subject "Project alpha". The system downloads the email trough pop3, parses the subject and sender. It then stores report.doc in /bob/alpha/

**Use case 2:**
Bob need to retrieve some things that he backed up. He sends an email with the subject "list files" and in the body, his password. the system then parses the body and subject, verifies that he wants a list of his files, verifies the passwords, and as it is correct, sends BOB a list of all his files, with the associated projects.
Bob then reads the email and sends another, this time with the subject "get alpha/report.doc" and his password in the body. the system receives the email, parses the body and the subject, checks for the password, and sends an e-mail to BOB with the report.doc attached.

**Use case 3:**
This time bob needs a full restore from the alpha project. He send an email with his password on the body and "get all alpha" on the subject. the systems receives it, parses, and then recursively selects from all users folders, all files in /USER/alpha, zips them, worrying about a max 5 MB per email and sends as many mails as needed so Bob will receive the files he needs.


I hope you people can understand.

Thank you very much.

---

### Post by freebeer on 2008-07-30
Well, what you envision is a rather specialized arrangement.  I still think Zimbra/Zimbra Desktop will achieve what you really want to do - remotely handle/share files (calendars, too, but you didn't specify that).  At least it seems to fit the bill as far as storing/retrieving/sharing files, email, calendars, etc.

I'm in the very early stages of checking it out myself, so I'm not up on all the intracasies of what it can and can't do.

---

### Post by Biochem on 2008-07-30
> **Proto_ said:**
> 

**Use case 2:**
Bob need to retrieve some things that he backed up. He sends an email with the subject "list files" and in the body, **his password**. the system then parses the body and subject, verifies that he wants a list of his files, verifies the passwords, and as it is correct, sends BOB a list of all his files, with the associated projects.
Bob then reads the email and sends another, this time with the subject "get alpha/report.doc" and his password in the body. the system receives the email, parses the body and the subject, checks for the password, and sends an e-mail to BOB with the report.doc attached.

**Use case 3:**
This time bob needs a full restore from the alpha project. He send an email with **his password** on the body and "get all alpha" on the subject. the systems receives it, parses, and then recursively selects from all users folders, all files in /USER/alpha, zips them, worrying about a max 5 MB per email and sends as many mails as needed so Bob will receive the files he needs.


**Use case 4:**
Competitors Billy happen to have gotten a copy of Bob's request. Since emails are not encrypted in transit he now has Bob's password and therefore access to project alpha, beta, and gamma giving him a serious competitive advantage allowing his compagny to outbid them. Bob's compagny is now bankrupt.

**Use case 5**
Project alpha contains very sensitive clients informations. client using inspecting all packet leaving it's network finds out Bob sent the alpha/report.doc and password to retrieve all other files from the alpha project. Bob's immediately get's kicked out of the office under armed escort and body cavity search. Bob's compagny get sued and is now bankrupt.

In other word be very carefull on how you do it. Security might be an issue here. How about configuring an ssh server on the pop3 port? You would be able to access your file using portable winscp from any computer you like without the need of special software and it is very secure (especially if you use key based authentication).

---

