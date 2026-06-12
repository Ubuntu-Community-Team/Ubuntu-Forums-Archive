---
title: "Can't create ldapi connection ebox-usersandgroups / ebox-samba"
date: 2008-04-13
forum: Server Platforms
---

### Post by curtishall on 2008-04-13
I had ebox-samba / ebox-usersandgroups working at one time.  Then...something happened (I don't know what) and now the module is loaded however when I try to add / edit a user or save the samba configuration I get:

Can't create ldapi connection

\n$VAR1 = bless( {
                 '-stacktrace' => 'Can\'t create ldapi connection at /usr/share/perl5/EBox/Ldap.pm line 113
	EBox::Ldap::ldapCon(\'EBox::Ldap=HASH(0x33bd680)\') called at /usr/share/perl5/EBox/Ldap.pm line 233
	EBox::Ldap::search(\'EBox::Ldap=HASH(0x33bd680)\', \'HASH(0x2ad0f50)\') called at /usr/share/perl5/EBox/UsersAndGroups.pm line 907
	EBox::UsersAndGroups::groups(\'EBox::UsersAndGroups=HASH(0x33bfd40)\') called at /usr/share/perl5/EBox/CGI/UsersAndGroups/Users.pm line 48
	EBox::CGI::UsersAndGroups::Users::_process(\'EBox::CGI::UsersAndGroups::Users=HASH(0x1ee9140)\') called at /usr/share/perl5/EBox/CGI/Base.pm line 254
	EBox::CGI::Base::run(\'EBox::CGI::UsersAndGroups::Users=HASH(0x1ee9140)\') called at /usr/share/perl5/EBox/CGI/Run.pm line 92
	EBox::CGI::Run::run(\'EBox::CGI::Run\', \'UsersAndGroups/Users\') called at /usr/share/ebox/cgi/ebox.cgi line 19
	ModPerl::ROOT::ModPerl::Registry::usr_share_ebox_cgi_ebox_2ecgi::handler(\'Apache2::RequestRec=SCALAR(0x1ee88d0)\') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
	eval {...} called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
	ModPerl::RegistryCooker::run(\'ModPerl::Registry=HASH(0x1ee89f0)\') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 170
	ModPerl::RegistryCooker::default_handler(\'ModPerl::Registry=HASH(0x1ee89f0)\') called at /usr/lib/perl5/ModPerl/Registry.pm line 31
	ModPerl::Registry::handler(\'ModPerl::Registry\', \'Apache2::RequestRec=SCALAR(0x1ee88d0)\') called at -e line 0
	eval {...} called at -e line 0
',
                 '-file' => '/usr/share/perl5/EBox/Ldap.pm',
                 '-text' => 'Can\'t create ldapi connection',
                 '-line' => 113,
                 '-package' => 'EBox::Ldap'
               }, 'EBox::Exceptions::Internal' );

I've removed ebox-samba and ebox-usersandgroups along with removing slapd (purging during the removal) and reinstalling however I still can't see to fix this.  I've also tried to reconfigure slapd / libpam-ldap .

I'm really out of ideas and would love to have some suggestions

---

### Post by foolano on 2008-04-14
Did you reboot the machine? If you did and you didn't have the last available version of slapd, it's probably that slapd didn't start properly at boot time. Make sure you update your slapd package.

Anyway,  as you removed slapd now you have to initialise the openLDAP directory and configure samba again. You have to keep in mind that for eBox your slapd directory and samba have already been initialised. That initialisation takes place when you enable the module for first time. 

I have a script to set the service as not configured, this way you are able to go to *module status* and enable the module again.

This is the script:

```

#!/bin/perl

use EBox;
use EBox::Global;

EBox::init();

my $module = $ARGV[0];

unless (defined($module)) {
    print "Usage: $0 module";
    exit 1;
}

my $global = EBox::Global->getInstance();

unless ($global->modExists($module)) {
    print "Module $module doesn't exists";
}

my $mod = $global->modInstance($module);
$mod->st_set_bool('_serviceConfigured', undef);


```

You can also download it from [here]("http://people.warp.es/~javi/ebox-reconfigure-module.pl").

Once you have installed ebox-samba and ebox-usersandgroups again, run the above script as follows:

```

sudo ./ebox-reconfigure-module.pl users
sudo ./ebox-reconfigure-module.pl samba

```

Now you can go to *module status* and enable *users and groups* and *samba*

---

