---
title: "Apache .htaccess authentication... logout function??"
date: 2008-04-04
forum: Security Discussions
---

### Post by lambono on 2008-04-04
Hi guys,
Quick q for yas. 

I am using a .htaccess file to secure a directory.

```

AuthUserFile /path/.htpasswd
AuthGroupFile /dev/null
AuthName "Private Area"
AuthType Basic
<Limit GET POST>
require user name
</Limit>

```

This works fine and the user can login with their name and password. 

However if they close the page, then return to it they do not have to enter their details again. 

Is it possible to have a button the user can click to logout of the site? :confused:

Thanks in advance for your help!

---

### Post by kidders on 2008-04-05
Hi there,

> **lambono said:**
> if they close the page, then return to it they do not have to enter their details again.This is by design. Basic authentication has no concept of logging in or out, because the idea of a session doesn't exist. Once a server sends its first HTTP 401 response, browsers are allowed to assume the authorisation details are required for every subsequent request, so the server never gets a chance to tell the client not to send them any more.

For most browsers, the only way to stop them sending authorisation information is to restart them.

---

### Post by lambono on 2008-04-06
Hi Kidders,
Thanks for that. 
Not quite the answer I would have liked... but at least now I know ;)

Lambono

---

### Post by kidders on 2008-04-06
No problem. Depending on whether you really meant to use the word "secure" in your o/p, you might want to check out HTTP's digest authentication ... basic authentication per se provides no security. The digest scheme is a little more robust.

Perhaps what you're *really* after is server-side session-based authentication though. You should be able to find tutorials for a variety of languages (eg php, coldfusion, perl, etc.) easily enough, and that'd give you the ability to log people in and out.

---

### Post by HermanAB on 2008-04-06
Yup, if you want security, use HTTPS on port 443.

---

### Post by lambono on 2008-04-12
Hi Guys,
Gonna have to stick with basic Auth at the min.

Perhaps you could help me with one more thing....

I have some MP3 files in the protected directory.
I a user clicks the link to the file they are first asked to provide their details and then the music will play in their browser plugin. 

However, if they right click the link and hit 'Save Target As' (before they authenticate themselves) then they will not be able to download the file.

Is there any way to prompt for authentication, before they save a file if they have not logged in already? 

Hope that makes sense! 

Hope to hear form you soon as I need an answer ASAP

Thanks!

---

### Post by kidders on 2008-04-12
Hey again,

That's interesting. I tested Opera, Safari & Firefox, and Firefox seems to be the only one (at least of these three) with this problem. It strikes me as a potential bug, since Firefox appears to disregard the HTTP 401 header sent by my web server. Having said that, it strikes me as unlikely that we are the first to notice such a basic flaw ... perhaps Mozilla don't consider it a bug. There is a variety of technical issues I didn't take the time to test that may turn out to make the counter-intuitive behaviour you noticed (ie downloading & saving the text of the authorisation request as though it were the requested file) in technical compliance with the HTTP protocol standards.

Anyhow, there is no way to solve this problem ... the best you can do is work around it. You could...[LIST]
[*]Try asking for authorisation information sooner, so it's already being included in request headers by the time users try to download your MP3s.
[*]Switch to a browser that behaves more sensibly.
[*]Switch to a more robust authentication mechanism.
[/LIST]

Unfortunately, pure HTTP-based authorisation gives you no control whatsoever over how clients interact with your server. Each browser has its own slightly different take on how this aspect of the HTTP standards is to be applied, which you just have to live with.

---

