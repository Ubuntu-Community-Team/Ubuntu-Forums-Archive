---
title: "How to make .htaccess for ssl login page and redirect to http after login"
date: 2008-08-06
forum: Server Platforms
---

### Post by taicyber on 2008-08-06
Below is my folder structure
When user comes to

1. "/mysite" the index.php in mysite will redirect to /mysqite/data/modules/mysite1/interfaces/login.php
So I made .htaccess here

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

2. login.php page
<form class="loginForm" action="../../../../login_trainee.php" method="POST" id="Login">

The data of user should be encrypted and send to login_trainee.php which is in "/mysite"
I think I have to make .htaccess for "/interfaces" but the problem is
after login user should return to use http in the rest of site even if in "/interfaces" too.

Before login : https..../mysqite/data/modules/mysite1/interfaces/login.php
After login :  http...../mysqite/data/modules/mysite1/interfaces/index.php

Anyone have some idea about this?
thank you

---

