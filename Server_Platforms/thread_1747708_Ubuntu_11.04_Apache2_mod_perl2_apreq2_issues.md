---
title: "Ubuntu 11.04 Apache2 mod_perl2 apreq2 issues"
date: 2011-05-02
forum: Server Platforms
---

### Post by yakubori on 2011-05-02
Getting the following error in apache_error.log:

```

[Mon May 02 21:43:26 2011] [error] [client 127.0.0.1] Can't locate object method "loglevel" via package "Apache2::ServerRec" at /var/project/lib/perl/Project.pm line 13.\n

```Here is some system info:

```

ls -l /etc/apache2/mods-enabled/perl.load 
lrwxrwxrwx 1 root root 27 2011-05-02 20:38 /etc/apache2/mods-enabled/perl.load -> ../mods-available/perl.load

ls -l /etc/apache2/mods-enabled/apreq.load 
lrwxrwxrwx 1 root root 28 2011-05-02 20:45 /etc/apache2/mods-enabled/apreq.load -> ../mods-available/apreq.load

apache2ctl -M
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 apreq_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgid_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 perl_module (shared)
 reqtimeout_module (shared)
 setenvif_module (shared)
 status_module (shared)
Syntax OK

ls -gG /var/
drwxr-xr-x  7 4096 2011-05-02 21:37 project

ls -gG /var/project/
total 20
drwxr-xr-x 2 4096 2011-05-02 21:38 bin
drwxr-xr-x 2 4096 2011-05-02 21:37 conf
drwxr-xr-x 2 4096 2011-05-02 21:37 doc
drwxr-xr-x 3 4096 2011-05-02 21:37 lib
drwxr-xr-x 2 4096 2011-05-02 21:38 www

ls -gG /var/project/bin/startup.pl 
-rwxr-xr-x 1 87 2011-05-02 21:38 /var/project/bin/startup.pl

```Here is the relevant apache conf:

```

PerlRequire /var/project/bin/startup.pl
    Alias /project/ "/var/project/www/"
    <Location /project>
        SetHandler modperl
        PerlResponseHandler Project
        Options -Indexes
        Order allow,deny
        Allow from all
    </Location>

```Here is startup.pl:

```

#!/usr/bin/env perl

use warnings;
use strict;

use lib qw(/var/project/lib/perl);

1;

```Finally, here is the handler module (a simple test derived from an apache/mod_perl book).

```

package Project;

use warnings;
use strict;

use Data::Dumper;
use Apache2::Const -compile => qw(OK LOG_DEBUG);
use Apache2::Request;

sub handler {
    my $r = shift;
    
    $r->server->loglevel(Apache2::Const::LOG_DEBUG);

    $r->log->debug('DEBUG: ' . Dumper($r));

    $r->content_type('text/html');
    $r->print('<h1>Test Handler</h1>');

    return Apache2::Const::OK;
}

1;

```I've been able to get this working in a Gentoo environment. However, I would really like this to work in Ubuntu... ANY help would be appreciated.

---

### Post by yakubori on 2011-05-04
bump. for the love of god, bump...

I have gone as far as to compile apache2, modperl2, and apreq2 from source, and STILL get the same error...

---

### Post by yakubori on 2011-05-05
Making progress... I found that, with the mod_perl modules, just because something is blessed as one of them does NOT mean they have been loaded. In my case:

```

use Apache2::RequestIO ();
use Apache2::ServerRec ();

```were required to be somewhere, so I added them to my startup.pl file. 

NOTE: Everything was working in my Gentoo environment because I had another startup.pl file included (which pretty much used everything in the Apache2:: namespace) from another web service in my apache config.

So, everything worked in the compiled ubuntu 11.04 environment after I made that change! Here's the new startup.pl

```

#!/usr/bin/env perl

use strict;
use warnings;

use lib qw(/var/project/lib/perl);

use Apache2::ServerRec (); 
use Apache2::RequestRec (); 
use Apache2::RequestIO (); 

1;

```Now... new issues....

I got rid of all the compiled stuff and re-installed the required packages from apt, which gives me a threaded apache instance. So now, I see this:

```

[Thu May 05 17:55:03 2011] [error] [client 127.0.0.1] Can't run 'setting loglevel' in the threaded environment after server startup at /var/project/lib/perl/Project.pm line 13.\n

```It never ends...

I'm now trying to get THAT resolved... as always, if anyone can help, please do...

---

### Post by yakubori on 2011-05-05
OKAY! I GOT IT!!

You need to run apache with the mpm_prefork_module and NOT the mpm_worker_module (which is what will be installed if you simply install apache2 via apt).

This is easily fixed by running:

```

apt-get install apache2-mpm-prefork

```...which will replace apache2-mpm-worker for you.

You can verify which mpm is compiled by running:

```

/usr/sbin/apache2ctl -M |grep -i mpm
Syntax OK
 mpm_prefork_module (static)

```The word around the campfire is to avoid apache threads when using mod_perl...

---

