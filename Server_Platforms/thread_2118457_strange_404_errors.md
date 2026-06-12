---
title: "strange 404 errors"
date: 2013-02-21
forum: Server Platforms
---

### Post by Toriku on 2013-02-21
Background Story:
 After making some changes to the company website last year, I wrote a script to email me when an error 404 occurs, so I can find out if I missed anything and the customers can find what they are looking for... At the time it helped me find a picture that wasn't loading...

What Happened:
 Today I received 52 error 404 emails in about 25 seconds just after half past twelve, each from what appeared to be (according to a few pages on Google search) a Chinese IP address. 222.186.26.32.
 It appeared to be looking for login pages on the website:
 The addresses it was attempting to access are as follows:

```
[http://mydomain.co.uk/member/join.php](http://mydomain.co.uk/member/join.php)
[http://mydomain.co.uk/User/Register.aspx](http://mydomain.co.uk/User/Register.aspx)
[http://mydomain.co.uk/join.php](http://mydomain.co.uk/join.php)
[http://mydomain.co.uk/register.php](http://mydomain.co.uk/register.php)
[http://mydomain.co.uk/signup.php](http://mydomain.co.uk/signup.php)
[http://mydomain.co.uk/member/register](http://mydomain.co.uk/member/register)
[http://mydomain.co.uk/YaBB.pl/](http://mydomain.co.uk/YaBB.pl/)
[http://mydomain.co.uk/YaBB.cgi/](http://mydomain.co.uk/YaBB.cgi/)
[http://mydomain.co.uk/signup.php](http://mydomain.co.uk/signup.php)
[http://mydomain.co.uk/join.php](http://mydomain.co.uk/join.php)
[http://mydomain.co.uk/signup](http://mydomain.co.uk/signup)
[http://mydomain.co.uk/CreateUser.asp](http://mydomain.co.uk/CreateUser.asp)
[http://mydomain.co.uk/signup](http://mydomain.co.uk/signup)
[http://mydomain.co.uk/join_form.php](http://mydomain.co.uk/join_form.php)
[http://mydomain.co.uk/join.php](http://mydomain.co.uk/join.php)
[http://mydomain.co.uk/register.aspx](http://mydomain.co.uk/register.aspx)
[http://mydomain.co.uk/account/register.php](http://mydomain.co.uk/account/register.php)
[http://mydomain.co.uk/signup.php](http://mydomain.co.uk/signup.php)
[http://mydomain.co.uk/member/index_do.php?fmdo=user&dopost=regnew](http://mydomain.co.uk/member/index_do.php?fmdo=user&dopost=regnew)
[http://mydomain.co.uk/register.cgi](http://mydomain.co.uk/register.cgi)
[http://mydomain.co.uk/cgi-bin/register.cgi](http://mydomain.co.uk/cgi-bin/register.cgi)
[http://mydomain.co.uk/register.php](http://mydomain.co.uk/register.php)
[http://mydomain.co.uk/ucp.php?mode=register](http://mydomain.co.uk/ucp.php?mode=register)
[http://mydomain.co.uk/profile.php?mode=register&agreed=true&coppa=0](http://mydomain.co.uk/profile.php?mode=register&agreed=true&coppa=0)
[http://mydomain.co.uk/register.php](http://mydomain.co.uk/register.php)
[http://mydomain.co.uk/register.php](http://mydomain.co.uk/register.php)
[http://mydomain.co.uk/registration_rules.asp?FID=0](http://mydomain.co.uk/registration_rules.asp?FID=0)
[http://mydomain.co.uk/signup.php](http://mydomain.co.uk/signup.php)
[http://mydomain.co.uk/signup.php](http://mydomain.co.uk/signup.php)
[http://mydomain.co.uk/bokeindex.asp](http://mydomain.co.uk/bokeindex.asp)
[http://mydomain.co.uk/reg.asp](http://mydomain.co.uk/reg.asp)
[http://mydomain.co.uk/login.php?action=quit](http://mydomain.co.uk/login.php?action=quit)
[http://mydomain.co.uk/login.php](http://mydomain.co.uk/login.php)
[http://mydomain.co.uk/CreateUser.asp](http://mydomain.co.uk/CreateUser.asp)
[http://mydomain.co.uk/login.php](http://mydomain.co.uk/login.php)
[http://mydomain.co.uk/register.php](http://mydomain.co.uk/register.php)
[http://mydomain.co.uk/logging.php?action=login](http://mydomain.co.uk/logging.php?action=login)
[http://mydomain.co.uk/reg.asp](http://mydomain.co.uk/reg.asp)
[http://mydomain.co.uk/reg.asp](http://mydomain.co.uk/reg.asp)
[http://mydomain.co.uk/tools/quicklogin.one](http://mydomain.co.uk/tools/quicklogin.one)
[http://mydomain.co.uk/signup/](http://mydomain.co.uk/signup/)
[http://mydomain.co.uk/(0014)about:internet](http://mydomain.co.uk/(0014)about:internet)
[http://mydomain.co.uk/modules.php?app=user_reg](http://mydomain.co.uk/modules.php?app=user_reg)
[http://mydomain.co.uk/member.php?mod=register](http://mydomain.co.uk/member.php?mod=register)
[http://mydomain.co.uk/member.php?mod=logging&action=login](http://mydomain.co.uk/member.php?mod=logging&action=login)
[http://mydomain.co.uk/login.php](http://mydomain.co.uk/login.php)
[http://mydomain.co.uk/sign_up.html](http://mydomain.co.uk/sign_up.html)
[http://mydomain.co.uk/user/register](http://mydomain.co.uk/user/register)
[http://mydomain.co.uk/tiki-register.php](http://mydomain.co.uk/tiki-register.php)
[http://mydomain.co.uk/wp-login.php?action=register](http://mydomain.co.uk/wp-login.php?action=register)
[http://mydomain.co.uk/signup](http://mydomain.co.uk/signup)
[http://mydomain.co.uk/signup](http://mydomain.co.uk/signup)

```


Has anyone else encountered this before? Or have any idea what it is?

---

### Post by SeijiSensei on 2013-02-21
Sure, it's an intrusion attempt.  It's looking to see if you have any web applications with known vulnerabilities running.

Machines like this I dump into the "evil" list on my firewall and block them entirely.

I use sessions for most sites and pass the session's cookie ID in a GET string if the browser refuses cookies.  I see the occasional URL with things like "session_name=http://www.example.com" and other garbage.  I now test to see if the cookie string matches some requirements and bail on any connection that fails to pass the test.  I also rarely use anything other than index.php as the page URL and control content through passed parameters.  So I would never have a login.php, but I might have an index.php?go=login.  Usually automated scanners won't detect things like that.  They'll just move on to the next potential victim.

---

### Post by Toriku on 2013-02-21
I suspected that may have been the case, I'll bear that in mind in future; thanks

---

