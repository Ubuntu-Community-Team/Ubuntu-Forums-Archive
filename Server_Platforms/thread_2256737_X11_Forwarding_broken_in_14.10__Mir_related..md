---
title: "X11 Forwarding broken in 14.10?  Mir related."
date: 2014-12-14
forum: Server Platforms
---

### Post by Tony.Mercury on 2014-12-14
Hey everyone.

I've installed Ubuntu Server 14.10 with a minimal install with just the base packages, virtual host packages + virt-manager in hopes to have a X11 Forwarding session using PuTTY/Xming as my Windows SSH client.  This has worked previously with numerous distros and previous versions of Ubuntu Server but unfortunately this seems to be broken now and I can't see to find any help on the subject.

```
root@Server:/home/tony# PuTTYNG X11 proxy: wrong authorisation protocol attempted** (virt-manager:5018): WARNING **: Could not open X display
PuTTYNG X11 proxy: wrong authorisation protocol attemptedgdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory


(virt-manager:5018): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_settings_get_style_cascade: assertion 'GTK_IS_SETTINGS (settings)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed


(virt-manager:5018): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
/usr/lib/python2.7/dist-packages/gi/overrides/__init__.py:175: Warning: invalid (NULL) pointer instance
  return super_init_func(self, **new_kwargs)
/usr/lib/python2.7/dist-packages/gi/overrides/__init__.py:175: Warning: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
  return super_init_func(self, **new_kwargs)


(virt-manager:5018): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(virt-manager:5018): Gtk-CRITICAL **: _gtk_settings_get_style_cascade: assertion 'GTK_IS_SETTINGS (settings)' failed
^C
```

X11 Forwarding is enabled in the SSHd_config as well as double checking my PuTTY session settings which are the same settings I've used previously.  At the beginning of the error it's clear that it's some how related to Mir and was wondering if I can remove Mir or at least force it to use the standard Xserver?

Any help would be appreciated.

---

### Post by tgalati4 on 2014-12-14
I was under the impression that X-forwarding was one of the features that was lost when moving to Mir.  Either it is difficult to implement, or just not implemented yet.  I'm not sure the X-Windows layer compatibility supports X-forwarding either.

What prevents you from using 14.04?

---

### Post by kevdog on 2014-12-15
Hmm, didn't know in 14.10 Mir was used as default over X-windowing system.  Learn something everyday.   If your running a server I'd really stick with 14.04.

---

