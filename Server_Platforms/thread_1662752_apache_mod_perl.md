---
title: "apache mod_perl"
date: 2011-01-08
forum: Server Platforms
---

### Post by vortmax on 2011-01-08
I'm attempting to get mod_perl to write a dynamic config file.  The script parses /home to make a list of all user home dirs.  Then it creates a virtual host for each of them.  I can reload apache all I want, and it does not throw an error, but the virtual hosts do not work, and checking them with 'apache2ctl -S' doesn't show them as being active.  However, if I purposely insert a syntax error into the file, it errors out on reload (so I know the perl code is being executed).

Here's my code:

```


<Perl>
my(%Location);

my @dirs = `ls -1 /home/`;
chomp(@dirs);

foreach my $dir (@dirs) {

  push @{$VirtualHost{"*:80"} },
      {
        'ServerAdmin' => 'xxxxxxxxxx',
        'DocumentRoot' => '/var/www/SVN/',
        'AddExternalAuth' => 'pwauth pipe',
        'directory' => {
           "/home/$dir/.repos" => {
              'Options' => 'Indexes FollowSymLinks MultiViews',
              'AllowOverride' =>  'None',
              'Order' =>  'allow,deny',
              'allow from' => 'all',
              },
        },
        'Location' => {
           "/repos" => {
                    'DAV' => 'svn',
                    'SVNParentPath' =>  '/home/'.$dir.'/.repos/',
                    'SVNListParentPath' => 'on',
                    'AuthType' => 'Basic',
                    'Require' => 'valid-user',
                    'AuthName' => '"xxxxxxxxxxxx"',
                    'AuthBasicProvider' => 'external',
                    'AuthExternal' => 'pwauth',
                     },
          },

   };
};
</Perl>

```

I've followed all of the guides I've seen online to no success.  It seems I could write explicit 'print' statements to write the file out, but according to the documentation, mod_perl should parse those specific variables and know what they mean.

---

### Post by vortmax on 2011-01-09
I managed to get it working and thought I'd share.  It must be a peculiarity with perl I'm not familiar with.  Instead of using push() to append entries to the array, I added them explicitly:

```

<Perl>
my(%Location);

my @dirs = `ls -1 /home/`;
chomp(@dirs);
my $i = 0;
foreach my $dir (@dirs) {

  $VirtualHost[$i]{"*:80"} =
      {
        'ServerAdmin' => 'xxxxxxxxxx',
        'DocumentRoot' => '/var/www/SVN/',
        'AddExternalAuth' => 'pwauth pipe',
        'directory' => {
           "/home/$dir/.repos" => {
              'Options' => 'Indexes FollowSymLinks MultiViews',
              'AllowOverride' =>  'None',
              'Order' =>  'allow,deny',
              'allow from' => 'all',
              },
        },
        'Location' => {
           "/repos" => {
                    'DAV' => 'svn',
                    'SVNParentPath' =>  '/home/'.$dir.'/.repos/',
                    'SVNListParentPath' => 'on',
                    'AuthType' => 'Basic',
                    'Require' => 'valid-user',
                    'AuthName' => '"xxxxxxxxxxxx"',
                    'AuthBasicProvider' => 'external',
                    'AuthExternal' => 'pwauth',
                     },
          },

   };
$i++
};
</Perl>

```

---

