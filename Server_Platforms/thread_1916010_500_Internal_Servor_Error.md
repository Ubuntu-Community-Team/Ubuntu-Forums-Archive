---
title: "500 Internal Servor Error"
date: 2012-01-27
forum: Server Platforms
---

### Post by MonkyGwen on 2012-01-27
Hi everybody,

I've installed lamp withe my ubuntu 10.04 version. I've made a website with php, mysql, ...
All was ok.
Now I try to make a forum. My problem is the 500 Internal Servor Error that never cames before. I don't know what is the problem and where to find the error file.
Could you help me please?:confused:

Here is what the fierbug console gives me as informations:
DateFri, 27 Jan 2012 12:33:21 GMTServerApache/2.2.14 (Ubuntu)X-Powered-ByPHP/5.3.2-1ubuntu4.11ExpiresThu, 19 Nov 1981 08:52:00 GMTCache-Controlno-store, no-cache, must-revalidate, post-check=0, pre-check=0Pragmano-cacheVaryAccept-EncodingContent-EncodinggzipContent-Length294ConnectioncloseContent-Typetext/htmlRequêtevoir le code source
HostlocalhostUser-AgentMozilla/5.0 (X11; U; Linux i686; fr; rv:1.9.2.24) Gecko/20111107 Ubuntu/10.04 (lucid) Firefox/3.6.24Accepttext/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8Accept-Languagefr,fr-fr;q=0.8,en-us;q=0.5,en;q=0.3Accept-Encodinggzip,deflateAccept-CharsetISO-8859-1,utf-8;q=0.7,*;q=0.7Keep-Alive115Connectionkeep-aliveRefererhttp://localhost/private/voyageauboutdelafaim/forum/CookiePHPSESSID=1fccphschfmnstt9gnvqbm2lu5Cache-Controlmax-age=0

Here is what my error.log file gives me: [Fri Jan 27 14:16:45 2012] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_ENCAPSED_AND_WHITESPACE in /media/www-dev/private/voyageauboutdelafaim/forum/includes/constants.php on line 11, referer: [http://localhost/private/voyageauboutdelafaim/forum/](http://localhost/private/voyageauboutdelafaim/forum/)

and here is my code in constants.pdf : 
<?php 
define('VISITEUR',1); 
define('INSCRIT',2); 
define('MODO',3); 
define('ADMIN',4); 
 
define('ERR_IS_CO','Vous ne pouvez pas accéder à cette page si vous n\'êtes pas connecté'); 
define('ERR_FLOOD','Contrôle anti flood, vous ne pouvez poster que toutes les '.$config['temps_flood'].' sec.<br /> 
Veuillez attendre un moment puis recommencer'); 
define('ERR_AUTH_ADMIN','Vous \'avez pas les accès requis pour cette section.'); 
define('ERR_IS_NOT_CO','Opération refusée, vous devez être connecté!'); 
?>

---

### Post by jamesa00789 on 2012-01-27
Its a syntax error - check your code.

---

### Post by Lars Noodén on 2012-01-27
One trick is to have a terminal open and track additions to the logs. 

```

tail -f /var/log/apache2/error.log

```

---

### Post by MonkyGwen on 2012-01-27
> **jamesa00789 said:**
> Its a syntax error - check your code.
I'll give my code for the file identifiants.php. It's corrected. So the problem is other.

---

### Post by MonkyGwen on 2012-01-27
and after, what can I do? Your request in the prompt give me different things that can not be charged and anotherthat say that favicon.ico does not exist. I don't what favicon.ico is.
I'm lost. Anyway, thanx for your reaction.

---

