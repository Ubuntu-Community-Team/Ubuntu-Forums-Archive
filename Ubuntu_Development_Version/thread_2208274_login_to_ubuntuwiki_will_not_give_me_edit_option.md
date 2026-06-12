---
title: "login to ubuntuwiki will not give me edit option"
date: 2014-02-27
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-02-27
Not sure where to put this. Ubuntu Trusty will not allow me  edit options when using Trusty (but I can edit using Maveric .. etc..).  I logged on using SSO. Any ideas?

Regards..

---

### Post by cariboo on 2014-02-27
> **ventrical said:**
> Not sure where to put this. Ubuntu Trusty will not allow me  edit options when using Trusty (but I can edit using Maveric .. etc..).  I logged on using SSO. Any ideas?

Regards..

Which browser are you having problems with? There have been some security features enabled in both Firefox and Chromium that don't like some of what both the forum and the wiki's do as far as allowing us to edit pages. In Chromium there is a shield that pops up to the left of the bookmark button that needs to be clicked before some scripts will run. I don't use Firefox, but I know something similar has been enabled with it too.

---

### Post by ventrical on 2014-02-27
> **cariboo907 said:**
> Which browser are you having problems with? There have been some security features enabled in both Firefox and Chromium that don't like some of what both the forum and the wiki's do as far as allowing us to edit pages. In Chromium there is a shield that pops up to the left of the bookmark button that needs to be clicked before some scripts will run. I don't use Firefox, but I know something similar has been enabled with it too.


 I am using ff.

 thanks for your input. I'll check into that.

Regards..

---

### Post by Doug S on 2014-02-27
Also there was recent confusion about sso and launchpad accounts and the ability to edit wiki pages. Refer to [this page]("https://help.ubuntu.com/community/WikiGuide/Registration"), which was just re-written in the last few days.

---

### Post by ventrical on 2014-02-27
> **Doug S said:**
> Also there was recent confusion about sso and launchpad accounts and the ability to edit wiki pages. Refer to [this page]("https://help.ubuntu.com/community/WikiGuide/Registration"), which was just re-written in the last few days.

 Went there and it had nothing on SSO. I checked out ff configs . etc.. nothing there indicating any problems.

edit..

 I just keep getting bounced and when I do get to the testers-wiki I am logged in but it tells me it is immutable page. No edit privlidge - but in maveric ..  when I logg off I never close my tabs so when I load ff then  it auto logs me on with privlidges..

---

### Post by Doug S on 2014-02-27
> **ventrical said:**
> Went there and it had nothing on SSO. Aren't SSO and Ubuntu one the same thing? Anyway, getting "immutable page" is exactly what the wiki editors were trying to clarify and as discussed on [this e-mail thread]("https://lists.ubuntu.com/archives/ubuntu-doc/2014-February/018728.html") on the ubuntu-docs e-mail list.

Edit: Which page are you trying to edit?

---

### Post by slickymaster on 2014-02-27
> **Doug S said:**
> Also there was recent confusion about sso and launchpad accounts and the ability to edit wiki pages. Refer to [this page]("https://help.ubuntu.com/community/WikiGuide/Registration"), which was just re-written in the last few days.

Ventrical, another tool you can refer to is this thread in the Documentation Team ML which address the same issue: [https://lists.ubuntu.com/archives/ubuntu-doc/2014-February/018728.html](https://lists.ubuntu.com/archives/ubuntu-doc/2014-February/018728.html)

---

### Post by cariboo on 2014-02-27
I've checked with both Chromium and Firefox in Trusty Ubuntu and Trusty Xubuntu, I can log in and edit the page in all four instances.

---

### Post by ventrical on 2014-02-27
> **Doug S said:**
> Aren't SSO and Ubuntu one the same thing? Anyway, getting "immutable page" is exactly what the wiki editors were trying to clarify and as discussed on [this e-mail thread]("https://lists.ubuntu.com/archives/ubuntu-doc/2014-February/018728.html") on the ubuntu-docs e-mail list.

Edit: Which page are you trying to edit?

  The thing is , my launchpad account usrname&password and SSO are both different. What did I do wrong?



"Bottom line is: to edit a wiki page, a user must also have a launchpad ID?

I see, because I noticed that Launchpad and the SSO for Ubuntu One’s username and password are exactly the same. If this is correct, we might want to include this sort of information on our documentation team page somewhere.

John Kim
Ubuntu Contributor"

---

### Post by ventrical on 2014-02-27
> **cariboo907 said:**
> I've checked with both Chromium and Firefox in Trusty Ubuntu and Trusty Xubuntu, I can log in and edit the page in all four instances.

  This is my fault.  I recall during the big switch that there was a message about  rolling over our launchpad accounts. I didn't think nothing of it at the time, so , here I have two different account names and passwords that aren't syncing. Thing is I forget how to fix it. :(

---

### Post by BlinkinCat on 2014-02-27
> **ventrical said:**
> This is my fault.  I recall during the big switch that there was a message about  rolling over our launchpad accounts. I didn't think nothing of it at the time, so , here I have two different account names and passwords that aren't syncing. Thing is I forget how to fix it. :(

I have a separate Launchpad Account and a SSO Account which I use for everything else.

As far as I know this is normal.

Cheers - :p

Edit: On checking I find there is a similarity with my Launchpad Account and the SSO Account.

---

### Post by ventrical on 2014-02-27
Ok... @ All,

Thanks for bearing with me and following up on this.  I just had to re-log into launchpad with my SSO account info. At first it kept comming up that "this account already exists" but then I logged out and logged on with SSO account info - then- to the wiki log-on and now I have [edit] priv. However , now I have two launchpad accounts I think, one for twocamels and one for ventrical, so, my bugs will now be reported by ventrical because that's what synced in.


Regards..

---

### Post by Doug S on 2014-02-27
While your experience is fresh, how can [this page]("https://help.ubuntu.com/community/WikiGuide/Registration") be improved?

---

### Post by ventrical on 2014-02-27
> **Doug S said:**
> While your experience is fresh, how can [this page]("https://help.ubuntu.com/community/WikiGuide/Registration") be improved?


 I edited an amend in there. Thanks :)

[h=2]If you have both a Launchpad Account and SSO Account with different usernames and passwords[/h] 
[LIST=1]
[*]Go to [http://launchpad.net/](http://launchpad.net/) 

[*]Make sure you are logged out of your regular Launchpad Account. 
[*]Click the **Login** button. 

[*]Enter the e-mail address and password of your current SSO Account. 
[*]Click 'Login'.
[/LIST]


Regards..

---

### Post by Doug S on 2014-02-27
> **ventrical said:**
> I edited an amend in there.Thank you very much.

---

### Post by slickymaster on 2014-02-28
> **ventrical said:**
> <---snip---> However , now I have two launchpad accounts I think, one for twocamels and one for ventrical, so, my bugs will now be reported by ventrical because that's what synced in.
Regards..

ventrical, you can resolve this easily. There is a way to merge Launchpad accounts, see [here]("https://help.launchpad.net/YourAccount/Merging") how to do it.

---

### Post by ventrical on 2014-02-28
> **slickymaster said:**
> ventrical, you can resolve this easily. There is a way to merge Launchpad accounts, see [here]("https://help.launchpad.net/YourAccount/Merging") how to do it.

Ok... thanks very much for that memo.

Regards..

---

