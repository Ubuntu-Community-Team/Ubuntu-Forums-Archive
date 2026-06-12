---
title: "Weird PAM_USB behaviour?"
date: 2012-05-07
forum: Security
---

### Post by zero2xiii on 2012-05-07
Hay all,

I have this strange issue. I set up a back up usb unlocking device to keep in a safe place as emergancy access to my computer should it ever be needed. (It was needed in the past..).

Following [this]("https://github.com/aluzzardi/pam_usb/wiki/Getting-Started") and [this]("https://github.com/aluzzardi/pam_usb/wiki/Configuration") I have set up my config files like this:
/etc/pamusb.conf
```
<?xml version="1.0" ?><!--
pamusb.conf: Configuration file for pam_usb.

See http://www.pamusb.org/doc/configuring
--><configuration>
	<!-- Default options -->
	<defaults>
		<!-- Example:
			<option name="debug">true</option>
		-->
	</defaults>

	<!-- Device settings -->
	<devices>
		<!-- Example:
		Note: You should use pamusb-conf to add devices automatically.
		<device id="MyDevice">
			<vendor>SanDisk Corp.</vendor>
			<model>Cruzer Titanium</model>
			<serial>SNDKXXXXXXXXXXXXXXXX</serial>
			<volume_uuid>6F6B-42FC</volume_uuid>
			<option name="probe_timeout">10</option>
		</device>
		-->
	<device id="Watch">
	<serial>
		USB_Flash_Disk_2A691B004381286D-0:0
	</serial>
	<option name="one_time_pad">
		false
	</option>
</device></devices>


	<!-- User settings -->
	<users>
		<!-- Note: Use pamusb-conf to add a user, then you can tweak
		 	manually the configuration here if needed.
		-->

		<!-- Example:
			Authenticate user scox using "MyDevice", and configure pamusb-agent
			to automatically start/stop gnome-screensaver on key insertion and
			removal:
			<user id="scox">
				<device>MyDevice</device>
				<option name="quiet">true</option>
				<agent event="lock">gnome-screensaver-command -lock</agent>
				<agent event="unlock">gnome-screensaver-command -deactivate</agent>
			</user>

			Configure user root to authenticate using MyDevice, but update one
			time pads at every login (default is 1 hour):
			<user id="root">
				<device>MyDevice</device>
				<option name="pad_expiration">0</option>
			</user>
		-->
	<user id="zeroburn">
	<device>Watch</device>
	<option name="quiet">true</option>
	<agent event="unlock">gnome-screensaver-command -deactivate</agent>
</user></users>

	<!-- Services settings (e.g. gdm, su, sudo...) -->
	<services>
		<!-- Example: Speed up hotplugging by disabling one time pads -->
		<!--
		<service id="pamusb-agent">
			<option name="one_time_pad">false</option>
		</service>
		-->

		<!-- Disable output for 'su' (needed for gksu) -->
		<!--
		<service id="su">
			<option name="quiet">true</option>
		</service>
		-->
	</services>
</configuration>
```

/etc/pam.d/common-auth
```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
#auth	[success=2 default=ignore]	pam_unix.so nullok_secure
#auth	[success=1 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
auth    sufficient      pam_usb.so
auth    sufficient      pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional			pam_smbpass.so migrate
auth	optional			pam_cap.so 
# end of pam-auth-update config
```

Now this all works. On GUI login, pluging in the USB and clicking on the username I get logged in. (I didn't bother changing anything <censoring> since I don't see the need.) In a TTY (ctrl + alt + F1-6) it works aswell.

I can log in with the password when the usb device is not plugged in as normal (I want this). But here is the issue. I want to be able to disable the screen saver lock, (activated automaticaly after 2minutes of inactivity on the machine) and any other password requests from programs needing sudo access. However, when I am loged in with the password, and then plug in my usb device. My session get logged out, and then I can log in without the password. This happens whether the screen saver lock is active or not.

How can I change/solve this to unlock the computer from the current position. Such as disable the password requiring screen lock, allowing access to programs launched with gksudo or sudo from the terminal, without resetting the current session?

Thanks in advance.
Cherz

---

