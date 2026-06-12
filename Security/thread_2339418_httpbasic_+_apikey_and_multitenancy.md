---
title: "httpbasic + apikey and multitenancy"
date: 2016-10-08
forum: Security
---

### Post by marchello_lippi2 on 2016-10-08
Hi all,  
  
 I'm about to implement httpbasic + apikey authentication with multitenancy.  
 What I mean... I'd like to create procedure with input parameters  for username, password and apikey, so that users could use it with their  own credentials, not only with stored default creds.  
  
 Below is how it works in sql without multitenancy.

```

EXEC SYSADMIN.createConnection("name" => 'webservice1',  "jbossCLITemplateName" => 'name1',  "connectionOrResourceAdapterProperties" =>  'EndPoint=https://api.example.com/api/,SecurityType=HTTPBasic,AuthUserName=[EMAIL]',  "encryptedProperties" => 'AuthPassword=[PASSWORD]') ;; 
 EXEC SYSADMIN.createDataSource("name" => 'webservice1',  "translator" => 'name1', "modelProperties" => '',  "translatorProperties" => '', "encryptedModelProperties" => '',  "encryptedTranslatorProperties" => '') ;;

```

```

exec  webservice1.invokeHTTP(endpoint=>'2.0/checks',requestHeaders=>  App-Key: myapikey1  ,action=>'GET',requestContentType=>'application/xml')

```

Now I'm trying to create connection without authusername and authpassword and it does work

```

EXEC SYSADMIN.createConnection("name" => 'webservice1',  "jbossCLITemplateName" => 'name1',  "connectionOrResourceAdapterProperties" =>  'EndPoint=https://api.example.com/api/,SecurityType=HTTPBasic') ;; 
 EXEC SYSADMIN.createDataSource("name" => 'webservice1',  "translator" => 'name1', "modelProperties" => '',  "translatorProperties" => '', "encryptedModelProperties" => '',  "encryptedTranslatorProperties" => '') ;;

```

but then I'm trying to call my webservice with credentials entered manually

```

exec  webservice1.invokeHTTP(endpoint=>'2.0/checks',requestHeaders=>  AuthUserName: user1 || AuthPassword: pass1 || App-Key:  myapikey1,action=>'GET',requestContentType=>'application/xml')

```

and receive error:

> 
Server returned HTTP response code: 401 for URL: [https://api.example.com/api//2.0/test1**](https://api.example.com/api//2.0/test1**) http error stream***{"error":{"statuscode":401,"statusdesc":"Unauthorized","errormessage":"User credentials missing"}}


How do I pass username and password for httpbasic auth properly without need to recreate the connection for different user? 
 Please advise.

---

