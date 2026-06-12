---
title: "PHP4/PHP5 on Apache2"
date: 2008-03-21
forum: Server Platforms
---

### Post by hyper_ch on 2008-03-21
Hiho, I'm trying to run php4 (as cgi) and php5 (as module) on my apache2 server on debian etch 64bit (I know, it's not ubuntu server but it's pretty close ^^).

When I try to run a simple <? phpinfo(); ?> script with the php4-cgi I get this error:
```

Warning: Unexpected character in input: '' (ASCII=16) state=1 in /var/www/web3/html/cgi-bin/php4-cgi on line 2469

Parse error: syntax error, unexpected '*' in /var/www/web3/html/cgi-bin/php4-cgi on line 2469

```

But when I run the php4-cgi binary from the shell with the script it works fine:
```

./cgi-bin/php4-cgi phpinfo.php

```

I fail to see why it is running on the shell but not through the web. Any suggestions?

---

