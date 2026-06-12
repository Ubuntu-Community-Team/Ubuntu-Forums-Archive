---
title: "how to allow apache (user www-data) to use /bin/bash as the shell"
date: 2014-11-27
forum: Server Platforms
---

### Post by kaleshwar on 2014-11-27
I am trying to get the apache user (www-data) to use the /bin/bash shell so that it is able to use commands such as pushd and cd

I have tried 
```

usermod -s /bin/bash www-data

```
after a restart finger www-data gives
```

Shell: /bin/bash

```

the following php 

[PHP]
<?php
echo('<pre>');
exec('whoami',$out);
echo($out);
echo("\n");
$out=array();
exec('echo $SHELL',$out);
echo($out);
?>
[/PHP]
gives the follwoing

```

Array
(
     [0]=>www-data
)
Array
(
    [0]=>
)

```

how can I get apache to actually use the shell?
any help highly appreciated.

thanks.

---

### Post by SeijiSensei on 2014-11-27
Just because www-data doesn't have a value set for $SHELL doesn't mean Apache isn't using bash.  Something had to execute the "whoami" command, after all.

---

### Post by DigiAngel on 2014-11-28
MIght be a path thing:

```
[07:18:05 gateway:~$] which whoami
/usr/bin/whoami

[07:32:42 gateway:~$] which echo
/bin/echo
```

---

### Post by SeijiSensei on 2014-11-28
I looked at [http://php.net/manual/en/reserved.variables.environment.php](http://php.net/manual/en/reserved.variables.environment.php) and saw this comment:

If your $_ENV array is mysteriously empty, but you still see the variables when calling getenv() or in your phpinfo(), check your [http://us.php.net/manual/en/ini.core.php#ini.variables-order](http://us.php.net/manual/en/ini.core.php#ini.variables-order) ini setting to ensure it includes "E" in the string.

If I use getenv(), I get a value for SHELL:
```

<?php
echo "SHELL=".getenv('SHELL');
?>

```
returns "SHELL=/bin/bash".

---

