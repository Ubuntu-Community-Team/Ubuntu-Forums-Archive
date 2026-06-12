---
title: "E-mail server"
date: 2008-12-14
forum: Server Platforms
---

### Post by chris.raighn on 2008-12-14
Hello my friend has a total of 3 computers in his home. He uses Outlook 2003 on all three to send/receive email from his Verizon account. The problem is that each computer downloads three different sets of the same email, also his contacts are slightly different on the three. Is there a way to have 1 computer download the email (server) and then the three others access the email/contacts, thus only downloading 1 copy of email?


Thanks!  :p

---

### Post by hictio on 2008-12-15
What type of account does your friend use?
Can he switch to IMAP on Verizon?

---

### Post by chris.raighn on 2008-12-15
its a @Verizon.net email account associated with the DSL service. I believe its a POP3 account? He doesn't need a full fledged new email account, but something if possible to serve the emails to the 3 computers. Mainly to sync all of his contacts.

---

### Post by HermanAB on 2008-12-15
You could run Citadel and fetch mail from the Verizon server:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)
[http://www.citadel.org/doku.php/faq:favoriteclient:how_do_i_retrieve](http://www.citadel.org/doku.php/faq:favoriteclient:how_do_i_retrieve)

Installing Citadel takes about 20 minutes.  Adding Spam Assassin and ClamAV takes another 20 minutes or so.

Cheers,

Herman

---

### Post by CrucifiedEgo on 2008-12-15
Or he could set outlook to leave mail on the verizon server for x days.  Sometimes the simplest solution is best, even if it misses a chance to use linux.

[http://imgs.xkcd.com/comics/regular_expressions.png](http://imgs.xkcd.com/comics/regular_expressions.png)

---

### Post by MJN on 2008-12-15
Definitely check to see if Verizon support IMAP (a brief Google search suggests they do). IMAP was created to address this exact issue (multiple disparate access to the same e-mails) although it won't directly help with the single contacts list bit.
 
Even better, he will not just have access to the same Inbox from all machine/clients but also every e-mail sent regardless of which machine/client was used. Indeed this applies all folders (drafts, archives etc).
 
Mathew

---

### Post by chris.raighn on 2008-12-15
Thanks for the responses guys! I have been playing with IMAP server's for the Outlook contacts, but its so darn confusing! The contacts is his main pet peeve though. I bought a little sandbox computer to test it on too

[http://i5.ebayimg.com/02/i/001/23/b6/f641_1.JPG](http://i5.ebayimg.com/02/i/001/23/b6/f641_1.JPG)

---

### Post by chris.raighn on 2008-12-15
I'm sorry it was LDAP for the contacts. That is so confusing! How is Mozilla Thunderbird on address book sharing?

---

### Post by chris.raighn on 2008-12-15
I think I found a solution: Funambol  [URL="https://www.forge.funambol.org/"]https://www.forge.funambol.org/
[/URL]
for sharing the contacts, etc. Combined with IMAP, it should be cake!

Any other server's I can implement for 3 Windows XP machines? :lolflag:

---

### Post by MJN on 2008-12-16
I think you may be misunderstanding the use of IMAP here. The suggestion is to use Verizon's IMAP service i.e. set the clients to connect using IMAP and not POP3.
 
It doesn't require any server building on your part - it's simply a small change to the client configurations.
 
A potential workaround worth exploring to solve the contacts issue might be to have an e-mail sat in the Drafts folder (or any other for that matter) with his list of contacts in. This message can be edited from any client with the results instantly available to all the others.
 
Mathew

---

### Post by chris.raighn on 2008-12-18
Yes that was simply for the Contacts of outlook. He also wants a backup/file server too. I'll have to give that IMAP a try, as I'm snowed in at the moment! :p It's more of a project this server is. Just for fun.

---

