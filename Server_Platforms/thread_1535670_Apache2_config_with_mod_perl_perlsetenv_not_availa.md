---
title: "Apache2 config with mod_perl: perlsetenv not available in perlrequire script"
date: 2010-07-21
forum: Server Platforms
---

### Post by stevenvegt on 2010-07-21
I'm upgrading old debian servers to Ubuntu 10.04 and we have to upgrade from apache 1.x and mod_perl.

I've got (sort of) the following apache configuration:
```

<VirtualHost x.x.x.x:40080>

PerlSetEnv      BASE   /home/steven/foo/base

PerlPostConfigRequire   /home/steven/foo/handler.pl

<LocationMatch "(\.mhtml)$">
        SetHandler  perl-script
        PerlHandler Ech::Mason
</LocationMatch>

</virtualHost>

```In the handler I've got this:

```
use Data::Dumper;
print Dumper(\%ENV);
```With a apache2ctl start the output is:

```
$VAR1 = {
          'PATH' => '/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games',
          'MOD_PERL_API_VERSION' => '2',
          'MOD_PERL' => 'mod_perl/2.0.4'
        };
```As you can see, my BASE variable is not set in the %ENV. Does anybody knows why?

---

