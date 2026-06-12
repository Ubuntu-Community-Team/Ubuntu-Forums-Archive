---
title: "Cadence Test-Unity Auto Pilot"
date: 2012-11-26
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-26
Guitara wrote:


"If you are feeling adventurous, you can actually run all the unity testcases like this (this will take a LONG TIME!). 			 		"

  I am currently running Unity AutoPilot on one of my main installs . How long actually will this test run?

Can I stop the test while it is in progress and how do i do this?

Thanks.

---

### Post by kansasnoob on 2012-11-26
I may be wrong but I think they expect us to use either a dedicated machine or VM so time won't matter :confused:

I may try it later in the week when I can free up my production machine for at least 12 hours.

It may seem almost off-topic but have you ever run "System Testing"?

I suspect that's part of it and it's a total joke! It checks things that don't exist and when you say it's not pertinent things puke all over the place!!!

---

### Post by ventrical on 2012-11-26
It's impossible to capture all the bugs and report them in the tracker. 

```

unity-log: {{{
WARN  2012-11-26 11:35:47 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:35:47 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733
}}}


======================================================================
FAIL: test_panel_first_menu_show_works (unity.tests.test_panel.PanelKeyNavigationTests)
unity.tests.test_panel.PanelKeyNavigationTests.test_panel_first_menu_show_works (Single Monitor)
----------------------------------------------------------------------
_StringException: test-log: {{{
11:39:52.033 DEBUG panel:88 - Moving mouse away from panel.
11:39:52.034 DEBUG X11:292 - Moving mouse to position 720,34 with animation.
11:39:52.522 WARNING testcase:482 - Tried to close applicaton 'Calculator' but it wasn't running.
11:39:52.568 INFO testcase:443 - Starting application 'Calculator' with files [] in locale C
11:39:55.685 DEBUG X11:124 - Pressing keys 'Alt+F10' with delay 0.200000
11:39:55.685 DEBUG X11:208 - Sending press event for key: Alt_L
11:39:55.888 DEBUG X11:208 - Sending press event for key: F10
11:39:56.090 DEBUG X11:142 - Releasing keys 'Alt+F10' with delay 0.200000
11:39:56.091 DEBUG X11:211 - Sending release event for key: F10
11:39:56.292 DEBUG X11:211 - Sending release event for key: Alt_L
11:40:52.020 DEBUG X11:124 - Pressing keys 'Escape' with delay 0.200000
11:40:52.021 DEBUG X11:208 - Sending press event for key: Escape
11:40:52.223 DEBUG X11:142 - Releasing keys 'Escape' with delay 0.200000
11:40:52.224 DEBUG X11:211 - Sending release event for key: Escape
11:40:53.437 DEBUG panel:88 - Moving mouse away from panel.
11:40:53.437 DEBUG X11:292 - Moving mouse to position 720,34 with animation.
11:40:53.438 INFO __init__:69 - Checking system state for badly behaving test...
11:40:55.261 INFO __init__:111 - Test was well behaved.
11:40:55.267 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{
WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_panel.py", line 970, in test_panel_first_menu_show_works
    open_indicator = self.get_active_indicator()
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_panel.py", line 960, in get_active_indicator
    self.assertThat(self.panel.get_active_indicator, Eventually(NotEquals(None)))
MismatchError: ('After 10 seconds test failed: %s', 'None == None')


======================================================================
FAIL: test_home_lens_has_shopping_results (unity.tests.test_shopping_lens.ShoppingLensTests)
unity.tests.test_shopping_lens.ShoppingLensTests.test_home_lens_has_shopping_results
----------------------------------------------------------------------
_StringException: test-log: {{{
11:41:19.805 DEBUG dash:46 - Toggling dash visibility with Super key.
11:41:19.806 DEBUG X11:124 - Pressing keys 'Super' with delay 0.100000
11:41:19.806 DEBUG X11:208 - Sending press event for key: Super_L
11:41:19.909 DEBUG X11:142 - Releasing keys 'Super' with delay 0.100000
11:41:19.910 DEBUG X11:211 - Sending release event for key: Super_L
11:41:20.787 DEBUG X11:124 - Pressing keys 'Ctrl+a' with delay 0.200000
11:41:20.787 DEBUG X11:208 - Sending press event for key: Control_L
11:41:20.991 DEBUG X11:208 - Sending press event for key: a
11:41:21.193 DEBUG X11:142 - Releasing keys 'Ctrl+a' with delay 0.200000
11:41:21.194 DEBUG X11:211 - Sending release event for key: a
11:41:21.395 DEBUG X11:211 - Sending release event for key: Control_L
11:41:21.596 DEBUG X11:124 - Pressing keys 'Delete' with delay 0.200000
11:41:21.597 DEBUG X11:208 - Sending press event for key: Delete
11:41:21.799 DEBUG X11:142 - Releasing keys 'Delete' with delay 0.200000
11:41:21.799 DEBUG X11:211 - Sending release event for key: Delete
11:41:25.422 DEBUG X11:176 - Typing text 'playstation'
11:41:25.422 DEBUG X11:124 - Pressing keys 'p' with delay 0.100000
11:41:25.422 DEBUG X11:208 - Sending press event for key: p
11:41:25.526 DEBUG X11:142 - Releasing keys 'p' with delay 0.100000
11:41:25.527 DEBUG X11:211 - Sending release event for key: p
11:41:25.631 DEBUG X11:124 - Pressing keys 'l' with delay 0.100000
11:41:25.632 DEBUG X11:208 - Sending press event for key: l
11:41:25.735 DEBUG X11:142 - Releasing keys 'l' with delay 0.100000
11:41:25.736 DEBUG X11:211 - Sending release event for key: l
11:41:25.837 DEBUG X11:124 - Pressing keys 'a' with delay 0.100000
11:41:25.837 DEBUG X11:208 - Sending press event for key: a
11:41:25.940 DEBUG X11:142 - Releasing keys 'a' with delay 0.100000
11:41:25.940 DEBUG X11:211 - Sending release event for key: a
11:41:26.042 DEBUG X11:124 - Pressing keys 'y' with delay 0.100000
11:41:26.042 DEBUG X11:208 - Sending press event for key: y
11:41:26.145 DEBUG X11:142 - Releasing keys 'y' with delay 0.100000
11:41:26.145 DEBUG X11:211 - Sending release event for key: y
11:41:26.246 DEBUG X11:124 - Pressing keys 's' with delay 0.100000
11:41:26.247 DEBUG X11:208 - Sending press event for key: s
11:41:26.350 DEBUG X11:142 - Releasing keys 's' with delay 0.100000
11:41:26.350 DEBUG X11:211 - Sending release event for key: s
11:41:26.452 DEBUG X11:124 - Pressing keys 't' with delay 0.100000
11:41:26.452 DEBUG X11:208 - Sending press event for key: t
11:41:26.555 DEBUG X11:142 - Releasing keys 't' with delay 0.100000
11:41:26.555 DEBUG X11:211 - Sending release event for key: t
11:41:26.656 DEBUG X11:124 - Pressing keys 'a' with delay 0.100000
11:41:26.657 DEBUG X11:208 - Sending press event for key: a
11:41:26.760 DEBUG X11:142 - Releasing keys 'a' with delay 0.100000
11:41:26.760 DEBUG X11:211 - Sending release event for key: a
11:41:26.861 DEBUG X11:124 - Pressing keys 't' with delay 0.100000
11:41:26.861 DEBUG X11:208 - Sending press event for key: t
11:41:26.964 DEBUG X11:142 - Releasing keys 't' with delay 0.100000
11:41:26.965 DEBUG X11:211 - Sending release event for key: t
11:41:27.066 DEBUG X11:124 - Pressing keys 'i' with delay 0.100000
11:41:27.066 DEBUG X11:208 - Sending press event for key: i
11:41:27.169 DEBUG X11:142 - Releasing keys 'i' with delay 0.100000
11:41:27.169 DEBUG X11:211 - Sending release event for key: i
11:41:27.270 DEBUG X11:124 - Pressing keys 'o' with delay 0.100000
11:41:27.270 DEBUG X11:208 - Sending press event for key: o
11:41:27.373 DEBUG X11:142 - Releasing keys 'o' with delay 0.100000
11:41:27.374 DEBUG X11:211 - Sending release event for key: o
11:41:27.475 DEBUG X11:124 - Pressing keys 'n' with delay 0.100000
11:41:27.475 DEBUG X11:208 - Sending press event for key: n
11:41:27.577 DEBUG X11:142 - Releasing keys 'n' with delay 0.100000
11:41:27.578 DEBUG X11:211 - Sending release event for key: n
11:41:49.076 DEBUG dash:46 - Toggling dash visibility with Super key.
11:41:49.076 DEBUG X11:124 - Pressing keys 'Super' with delay 0.100000
11:41:49.076 DEBUG X11:208 - Sending press event for key: Super_L
11:41:49.179 DEBUG X11:142 - Releasing keys 'Super' with delay 0.100000
11:41:49.179 DEBUG X11:211 - Sending release event for key: Super_L
11:41:49.938 INFO __init__:69 - Checking system state for badly behaving test...
11:41:51.740 INFO __init__:111 - Test was well behaved.
11:41:51.746 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{
WARN  2012-11-26 11:41:31 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:32 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:34 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:36 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:38 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:40 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:42 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:43 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:45 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:47 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_shopping_lens.py", line 51, in test_home_lens_has_shopping_results
    self.assertThat(refresh_results_fn, Eventually(GreaterThan(1)))
MismatchError: ('After 10 seconds test failed: %s', '1 is not < 0')


======================================================================
FAIL: test_keynav_prev_selection_works (unity.tests.test_quicklist.QuicklistKeyNavigationTests)
unity.tests.test_quicklist.QuicklistKeyNavigationTests.test_keynav_prev_selection_works
----------------------------------------------------------------------
_StringException: Empty attachments:
  unity-log

test-log: {{{
11:42:07.720 INFO __init__:69 - Checking system state for badly behaving test...
11:42:09.434 INFO __init__:111 - Test was well behaved.
11:42:09.440 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_quicklist.py", line 207, in setUp
    self.assertThat(icon_refresh_fn, Eventually(Equals(None)))
MismatchError: ('After 10 seconds test failed: %s', 'None != <BamfLauncherIcon gedit.desktop id=24>')


======================================================================
FAIL: test_unhide_single_app (unity.tests.test_showdesktop.ShowDesktopTests)
unity.tests.test_showdesktop.ShowDesktopTests.test_unhide_single_app
----------------------------------------------------------------------
_StringException: test-log: {{{
11:44:00.676 INFO testcase:443 - Starting application 'Character Map' with files [] in locale C
11:44:02.766 INFO testcase:443 - Starting application 'Calculator' with files [] in locale C
11:44:05.167 INFO window_manager:30 - Entering show desktop mode.
11:44:05.168 DEBUG X11:124 - Pressing keys 'Ctrl+Super+d' with delay 0.200000
11:44:05.168 DEBUG X11:208 - Sending press event for key: Control_L
11:44:05.372 DEBUG X11:208 - Sending press event for key: Super_L
11:44:05.575 DEBUG X11:208 - Sending press event for key: d
11:44:05.779 DEBUG X11:142 - Releasing keys 'Ctrl+Super+d' with delay 0.200000
11:44:05.780 DEBUG X11:211 - Sending release event for key: d
11:44:05.985 DEBUG X11:211 - Sending release event for key: Super_L
11:44:06.188 DEBUG X11:211 - Sending release event for key: Control_L
11:44:18.762 INFO __init__:69 - Checking system state for badly behaving test...
11:44:20.656 INFO __init__:111 - Test was well behaved.
11:44:20.662 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{
WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_showdesktop.py", line 68, in test_unhide_single_app
    self.window_manager.enter_show_desktop()
  File "/usr/lib/python2.7/dist-packages/unity/emulators/window_manager.py", line 32, in enter_show_desktop
    self.showdesktop_active.wait_for(True)
  File "/usr/lib/python2.7/dist-packages/autopilot/introspection/dbus.py", line 169, in wait_for
    % (self.parent.__class__.__name__, self.name, failure_msg))
AssertionError: After 10 seconds test on WindowManager.showdesktop_active failed: True != dbus.Boolean(False, variant_level=1)


======================================================================
FAIL: test_launcher_switcher_prev_doesnt_show_shortcuts (unity.tests.launcher.test_switcher.LauncherSwitcherTests)
unity.tests.launcher.test_switcher.LauncherSwitcherTests.test_launcher_switcher_prev_doesnt_show_shortcuts (Single Monitor)
----------------------------------------------------------------------
_StringException: Empty attachments:
  unity-log

test-log: {{{
11:46:04.195 INFO testcase:316 - Setting compiz option 'num_launchers' in plugin 'unityshell' to 0
11:46:05.338 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
11:46:05.349 DEBUG launcher:266 - Starting Super+Tab switcher.
11:46:05.350 DEBUG X11:124 - Pressing keys 'Super' with delay 0.200000
11:46:05.350 DEBUG X11:208 - Sending press event for key: Super_L
11:46:05.553 DEBUG X11:124 - Pressing keys 'Tab' with delay 0.200000
11:46:05.553 DEBUG X11:208 - Sending press event for key: Tab
11:46:05.755 DEBUG X11:142 - Releasing keys 'Tab' with delay 0.200000
11:46:05.755 DEBUG X11:211 - Sending release event for key: Tab
11:46:18.365 INFO testcase:316 - Setting compiz option 'num_launchers' in plugin 'unityshell' to 0
11:46:18.370 INFO __init__:69 - Checking system state for badly behaving test...
11:46:20.148 INFO __init__:111 - Test was well behaved.
11:46:20.153 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
11:46:20.164 WARNING X11:191 - Releasing key 133 as part of cleanup call.
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/launcher/test_switcher.py", line 116, in test_launcher_switcher_prev_doesnt_show_shortcuts
    self.start_switcher_with_cleanup_cancel()
  File "/usr/lib/python2.7/dist-packages/unity/tests/launcher/test_switcher.py", line 34, in start_switcher_with_cleanup_cancel
    self.launcher_instance.switcher_start()
  File "/usr/lib/python2.7/dist-packages/unity/emulators/launcher.py", line 268, in switcher_start
    self._get_controller().key_nav_is_active.wait_for(True)
  File "/usr/lib/python2.7/dist-packages/autopilot/introspection/dbus.py", line 169, in wait_for
    % (self.parent.__class__.__name__, self.name, failure_msg))
AssertionError: After 10 seconds test on LauncherController.key_nav_is_active failed: True != dbus.Boolean(False, variant_level=1)


======================================================================
FAIL: test_alt_f4_doesnt_show_hud (unity.tests.test_hud.HudBehaviorTests)
unity.tests.test_hud.HudBehaviorTests.test_alt_f4_doesnt_show_hud
----------------------------------------------------------------------
_StringException: test-log: {{{
11:46:20.267 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
11:46:20.325 INFO testcase:445 - Starting application 'Calculator' with files []
11:46:23.198 DEBUG X11:124 - Pressing keys 'Alt+F4' with delay 0.050000
11:46:23.199 DEBUG X11:208 - Sending press event for key: Alt_L
11:46:23.252 DEBUG X11:208 - Sending press event for key: F4
11:46:23.304 DEBUG X11:142 - Releasing keys 'Alt+F4' with delay 0.050000
11:46:23.304 DEBUG X11:211 - Sending release event for key: F4
11:46:23.355 DEBUG X11:211 - Sending release event for key: Alt_L
11:46:26.055 DEBUG X11:124 - Pressing keys 'Escape' with delay 0.200000
11:46:26.055 DEBUG X11:208 - Sending press event for key: Escape
11:46:26.259 DEBUG X11:142 - Releasing keys 'Escape' with delay 0.200000
11:46:26.259 DEBUG X11:211 - Sending release event for key: Escape
11:46:26.776 INFO __init__:69 - Checking system state for badly behaving test...
11:46:28.823 INFO __init__:111 - Test was well behaved.
11:46:28.828 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{
WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_hud.py", line 137, in test_alt_f4_doesnt_show_hud
    self.assertFalse(self.hud.visible)
AssertionError: Boolean(True) is not false


======================================================================
FAIL: test_dash_to_hud_has_key_focus (unity.tests.test_hud.HudBehaviorTests)
unity.tests.test_hud.HudBehaviorTests.test_dash_to_hud_has_key_focus
----------------------------------------------------------------------
_StringException: test-log: {{{
11:46:28.943 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
11:46:29.385 DEBUG dash:46 - Toggling dash visibility with Super key.
11:46:29.385 DEBUG X11:124 - Pressing keys 'Super' with delay 0.100000
11:46:29.385 DEBUG X11:208 - Sending press event for key: Super_L
11:46:29.488 DEBUG X11:142 - Releasing keys 'Super' with delay 0.100000
11:46:29.489 DEBUG X11:211 - Sending release event for key: Super_L
11:46:30.390 DEBUG X11:124 - Pressing keys 'Ctrl+a' with delay 0.200000
11:46:30.390 DEBUG X11:208 - Sending press event for key: Control_L
11:46:30.593 DEBUG X11:208 - Sending press event for key: a
11:46:30.796 DEBUG X11:142 - Releasing keys 'Ctrl+a' with delay 0.200000
11:46:30.796 DEBUG X11:211 - Sending release event for key: a
11:46:30.998 DEBUG X11:211 - Sending release event for key: Control_L
11:46:31.199 DEBUG X11:124 - Pressing keys 'Delete' with delay 0.200000
11:46:31.200 DEBUG X11:208 - Sending press event for key: Delete
11:46:31.402 DEBUG X11:142 - Releasing keys 'Delete' with delay 0.200000
11:46:31.402 DEBUG X11:211 - Sending release event for key: Delete
11:46:33.124 DEBUG X11:124 - Pressing keys 'Alt' with delay 0.100000
11:46:33.124 DEBUG X11:208 - Sending press event for key: Alt_L
11:46:33.227 DEBUG X11:142 - Releasing keys 'Alt' with delay 0.100000
11:46:33.228 DEBUG X11:211 - Sending release event for key: Alt_L
11:46:34.000 DEBUG X11:176 - Typing text 'focus2'
11:46:34.000 DEBUG X11:124 - Pressing keys 'f' with delay 0.100000
11:46:34.000 DEBUG X11:208 - Sending press event for key: f
11:46:34.103 DEBUG X11:142 - Releasing keys 'f' with delay 0.100000
11:46:34.103 DEBUG X11:211 - Sending release event for key: f
11:46:34.204 DEBUG X11:124 - Pressing keys 'o' with delay 0.100000
11:46:34.205 DEBUG X11:208 - Sending press event for key: o
11:46:34.307 DEBUG X11:142 - Releasing keys 'o' with delay 0.100000
11:46:34.308 DEBUG X11:211 - Sending release event for key: o
11:46:34.411 DEBUG X11:124 - Pressing keys 'c' with delay 0.100000
11:46:34.411 DEBUG X11:208 - Sending press event for key: c
11:46:34.514 DEBUG X11:142 - Releasing keys 'c' with delay 0.100000
11:46:34.514 DEBUG X11:211 - Sending release event for key: c
11:46:34.616 DEBUG X11:124 - Pressing keys 'u' with delay 0.100000
11:46:34.616 DEBUG X11:208 - Sending press event for key: u
11:46:34.719 DEBUG X11:142 - Releasing keys 'u' with delay 0.100000
11:46:34.719 DEBUG X11:211 - Sending release event for key: u
11:46:34.820 DEBUG X11:124 - Pressing keys 's' with delay 0.100000
11:46:34.821 DEBUG X11:208 - Sending press event for key: s
11:46:34.923 DEBUG X11:142 - Releasing keys 's' with delay 0.100000
11:46:34.924 DEBUG X11:211 - Sending release event for key: s
11:46:35.025 DEBUG X11:124 - Pressing keys '2' with delay 0.100000
11:46:35.025 DEBUG X11:208 - Sending press event for key: 2
11:46:35.127 DEBUG X11:142 - Releasing keys '2' with delay 0.100000
11:46:35.128 DEBUG X11:211 - Sending release event for key: 2
11:46:49.971 DEBUG X11:124 - Pressing keys 'Escape' with delay 0.200000
11:46:49.972 DEBUG X11:208 - Sending press event for key: Escape
11:46:50.174 DEBUG X11:142 - Releasing keys 'Escape' with delay 0.200000
11:46:50.175 DEBUG X11:211 - Sending release event for key: Escape
11:46:50.601 INFO __init__:69 - Checking system state for badly behaving test...
11:46:52.398 INFO __init__:111 - Test was well behaved.
11:46:52.404 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{ERROR 2012-11-26 11:46:33 unity <unknown>:0 bamf_matcher_get_application_for_window: assertion `BAMF_IS_WINDOW(window)' failed}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_hud.py", line 212, in test_dash_to_hud_has_key_focus
    self.assertThat(self.hud.search_string, Eventually(Equals('focus2')))
MismatchError: After 10 seconds test on SearchBar.search_string failed: 'focus2' != dbus.String(u'', variant_level=1)


======================================================================
FAIL: test_ignore_key_events_on_hud (unity.tests.test_ibus.IBusTestsPinyinIgnore)
unity.tests.test_ibus.IBusTestsPinyinIgnore.test_ignore_key_events_on_hud
----------------------------------------------------------------------
_StringException: Empty attachments:
  unity-log

test-log: {{{
11:46:52.981 DEBUG X11:124 - Pressing keys 'Alt' with delay 0.100000
11:46:52.982 DEBUG X11:208 - Sending press event for key: Alt_L
11:46:53.084 DEBUG X11:142 - Releasing keys 'Alt' with delay 0.100000
11:46:53.085 DEBUG X11:211 - Sending release event for key: Alt_L
11:46:53.775 DEBUG X11:176 - Typing text 'a'
11:46:53.775 DEBUG X11:124 - Pressing keys 'a' with delay 0.100000
11:46:53.775 DEBUG X11:208 - Sending press event for key: a
11:46:53.878 DEBUG X11:142 - Releasing keys 'a' with delay 0.100000
11:46:53.879 DEBUG X11:211 - Sending release event for key: a
11:46:56.561 DEBUG X11:124 - Pressing keys 'Escape' with delay 0.200000
11:46:56.562 DEBUG X11:208 - Sending press event for key: Escape
11:46:56.764 DEBUG X11:142 - Releasing keys 'Escape' with delay 0.200000
11:46:56.765 DEBUG X11:211 - Sending release event for key: Escape
11:46:57.177 INFO __init__:69 - Checking system state for badly behaving test...
11:46:58.964 INFO __init__:111 - Test was well behaved.
11:46:58.969 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_ibus.py", line 208, in test_ignore_key_events_on_hud
    self.activate_ibus(self.hud.searchbar)
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_ibus.py", line 79, in activate_ibus
    self.assertThat(widget.im_active, Equals(False))
MismatchError: False != Boolean(True)


----------------------------------------------------------------------
Ran 461 tests in 5784.978s

FAILED (failures=80, errors=10, skipped=62)
dale@dale-desktop:~$ B

```

[http://packages.qa.ubuntu.com/qatracker/milestones/246/builds/28425/testcases/1466/results](http://packages.qa.ubuntu.com/qatracker/milestones/246/builds/28425/testcases/1466/results)

---

### Post by ventrical on 2012-11-26
> **kansasnoob said:**
> I may be wrong but I think they expect us to use either a dedicated machine or VM so time won't matter :confused:

I may try it later in the week when I can free up my production machine for at least 12 hours.

It may seem almost off-topic but have you ever run "System Testing"?

I suspect that's part of it and it's a total joke! It checks things that don't exist and when you say it's not pertinent things puke all over the place!!!

Yes .. I have tried that some time ago.  It is just too arduous for my time frame.

I would like to note in all fairness that I am impressed with how the Unity AutoPilot was working.  No ill effects to my desktop, but, as you can see in my report, the report ran off the terminal screen so I have no way in knowing how to authenticate validated bugs, just the ones that are reported from the copy&paste from terminal.


 There were two bugs reported:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1083227](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1083227)
[https://launchpad.net/bugs/522286091](https://launchpad.net/bugs/522286091)  (this later being a non-bug)

at the tracker .

 The two apparent bugs I have are:
*EDIT* these are not bugs, they are app numbers:
/application1754135733

754135733
522286091

so I am not sure if these are new bugs.

I'm still checking into this.

---

### Post by kansasnoob on 2012-11-26
> **ventrical said:**
> It's impossible to capture all the bugs and report them in the tracker. 

```

unity-log: {{{
WARN  2012-11-26 11:35:47 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:35:47 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:35:48 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733
}}}


======================================================================
FAIL: test_panel_first_menu_show_works (unity.tests.test_panel.PanelKeyNavigationTests)
unity.tests.test_panel.PanelKeyNavigationTests.test_panel_first_menu_show_works (Single Monitor)
----------------------------------------------------------------------
_StringException: test-log: {{{
11:39:52.033 DEBUG panel:88 - Moving mouse away from panel.
11:39:52.034 DEBUG X11:292 - Moving mouse to position 720,34 with animation.
11:39:52.522 WARNING testcase:482 - Tried to close applicaton 'Calculator' but it wasn't running.
11:39:52.568 INFO testcase:443 - Starting application 'Calculator' with files [] in locale C
11:39:55.685 DEBUG X11:124 - Pressing keys 'Alt+F10' with delay 0.200000
11:39:55.685 DEBUG X11:208 - Sending press event for key: Alt_L
11:39:55.888 DEBUG X11:208 - Sending press event for key: F10
11:39:56.090 DEBUG X11:142 - Releasing keys 'Alt+F10' with delay 0.200000
11:39:56.091 DEBUG X11:211 - Sending release event for key: F10
11:39:56.292 DEBUG X11:211 - Sending release event for key: Alt_L
11:40:52.020 DEBUG X11:124 - Pressing keys 'Escape' with delay 0.200000
11:40:52.021 DEBUG X11:208 - Sending press event for key: Escape
11:40:52.223 DEBUG X11:142 - Releasing keys 'Escape' with delay 0.200000
11:40:52.224 DEBUG X11:211 - Sending release event for key: Escape
11:40:53.437 DEBUG panel:88 - Moving mouse away from panel.
11:40:53.437 DEBUG X11:292 - Moving mouse to position 720,34 with animation.
11:40:53.438 INFO __init__:69 - Checking system state for badly behaving test...
11:40:55.261 INFO __init__:111 - Test was well behaved.
11:40:55.267 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{
WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:40:53 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_panel.py", line 970, in test_panel_first_menu_show_works
    open_indicator = self.get_active_indicator()
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_panel.py", line 960, in get_active_indicator
    self.assertThat(self.panel.get_active_indicator, Eventually(NotEquals(None)))
MismatchError: ('After 10 seconds test failed: %s', 'None == None')


======================================================================
FAIL: test_home_lens_has_shopping_results (unity.tests.test_shopping_lens.ShoppingLensTests)
unity.tests.test_shopping_lens.ShoppingLensTests.test_home_lens_has_shopping_results
----------------------------------------------------------------------
_StringException: test-log: {{{
11:41:19.805 DEBUG dash:46 - Toggling dash visibility with Super key.
11:41:19.806 DEBUG X11:124 - Pressing keys 'Super' with delay 0.100000
11:41:19.806 DEBUG X11:208 - Sending press event for key: Super_L
11:41:19.909 DEBUG X11:142 - Releasing keys 'Super' with delay 0.100000
11:41:19.910 DEBUG X11:211 - Sending release event for key: Super_L
11:41:20.787 DEBUG X11:124 - Pressing keys 'Ctrl+a' with delay 0.200000
11:41:20.787 DEBUG X11:208 - Sending press event for key: Control_L
11:41:20.991 DEBUG X11:208 - Sending press event for key: a
11:41:21.193 DEBUG X11:142 - Releasing keys 'Ctrl+a' with delay 0.200000
11:41:21.194 DEBUG X11:211 - Sending release event for key: a
11:41:21.395 DEBUG X11:211 - Sending release event for key: Control_L
11:41:21.596 DEBUG X11:124 - Pressing keys 'Delete' with delay 0.200000
11:41:21.597 DEBUG X11:208 - Sending press event for key: Delete
11:41:21.799 DEBUG X11:142 - Releasing keys 'Delete' with delay 0.200000
11:41:21.799 DEBUG X11:211 - Sending release event for key: Delete
11:41:25.422 DEBUG X11:176 - Typing text 'playstation'
11:41:25.422 DEBUG X11:124 - Pressing keys 'p' with delay 0.100000
11:41:25.422 DEBUG X11:208 - Sending press event for key: p
11:41:25.526 DEBUG X11:142 - Releasing keys 'p' with delay 0.100000
11:41:25.527 DEBUG X11:211 - Sending release event for key: p
11:41:25.631 DEBUG X11:124 - Pressing keys 'l' with delay 0.100000
11:41:25.632 DEBUG X11:208 - Sending press event for key: l
11:41:25.735 DEBUG X11:142 - Releasing keys 'l' with delay 0.100000
11:41:25.736 DEBUG X11:211 - Sending release event for key: l
11:41:25.837 DEBUG X11:124 - Pressing keys 'a' with delay 0.100000
11:41:25.837 DEBUG X11:208 - Sending press event for key: a
11:41:25.940 DEBUG X11:142 - Releasing keys 'a' with delay 0.100000
11:41:25.940 DEBUG X11:211 - Sending release event for key: a
11:41:26.042 DEBUG X11:124 - Pressing keys 'y' with delay 0.100000
11:41:26.042 DEBUG X11:208 - Sending press event for key: y
11:41:26.145 DEBUG X11:142 - Releasing keys 'y' with delay 0.100000
11:41:26.145 DEBUG X11:211 - Sending release event for key: y
11:41:26.246 DEBUG X11:124 - Pressing keys 's' with delay 0.100000
11:41:26.247 DEBUG X11:208 - Sending press event for key: s
11:41:26.350 DEBUG X11:142 - Releasing keys 's' with delay 0.100000
11:41:26.350 DEBUG X11:211 - Sending release event for key: s
11:41:26.452 DEBUG X11:124 - Pressing keys 't' with delay 0.100000
11:41:26.452 DEBUG X11:208 - Sending press event for key: t
11:41:26.555 DEBUG X11:142 - Releasing keys 't' with delay 0.100000
11:41:26.555 DEBUG X11:211 - Sending release event for key: t
11:41:26.656 DEBUG X11:124 - Pressing keys 'a' with delay 0.100000
11:41:26.657 DEBUG X11:208 - Sending press event for key: a
11:41:26.760 DEBUG X11:142 - Releasing keys 'a' with delay 0.100000
11:41:26.760 DEBUG X11:211 - Sending release event for key: a
11:41:26.861 DEBUG X11:124 - Pressing keys 't' with delay 0.100000
11:41:26.861 DEBUG X11:208 - Sending press event for key: t
11:41:26.964 DEBUG X11:142 - Releasing keys 't' with delay 0.100000
11:41:26.965 DEBUG X11:211 - Sending release event for key: t
11:41:27.066 DEBUG X11:124 - Pressing keys 'i' with delay 0.100000
11:41:27.066 DEBUG X11:208 - Sending press event for key: i
11:41:27.169 DEBUG X11:142 - Releasing keys 'i' with delay 0.100000
11:41:27.169 DEBUG X11:211 - Sending release event for key: i
11:41:27.270 DEBUG X11:124 - Pressing keys 'o' with delay 0.100000
11:41:27.270 DEBUG X11:208 - Sending press event for key: o
11:41:27.373 DEBUG X11:142 - Releasing keys 'o' with delay 0.100000
11:41:27.374 DEBUG X11:211 - Sending release event for key: o
11:41:27.475 DEBUG X11:124 - Pressing keys 'n' with delay 0.100000
11:41:27.475 DEBUG X11:208 - Sending press event for key: n
11:41:27.577 DEBUG X11:142 - Releasing keys 'n' with delay 0.100000
11:41:27.578 DEBUG X11:211 - Sending release event for key: n
11:41:49.076 DEBUG dash:46 - Toggling dash visibility with Super key.
11:41:49.076 DEBUG X11:124 - Pressing keys 'Super' with delay 0.100000
11:41:49.076 DEBUG X11:208 - Sending press event for key: Super_L
11:41:49.179 DEBUG X11:142 - Releasing keys 'Super' with delay 0.100000
11:41:49.179 DEBUG X11:211 - Sending release event for key: Super_L
11:41:49.938 INFO __init__:69 - Checking system state for badly behaving test...
11:41:51.740 INFO __init__:111 - Test was well behaved.
11:41:51.746 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{
WARN  2012-11-26 11:41:31 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:32 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:34 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:36 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:38 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:40 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:42 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:43 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:45 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
WARN  2012-11-26 11:41:47 unity.debug.debugdbusinterface DebugDBusInterface.cpp:234 Query '//ResultView[id=226]/*' Did not match anything.
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_shopping_lens.py", line 51, in test_home_lens_has_shopping_results
    self.assertThat(refresh_results_fn, Eventually(GreaterThan(1)))
MismatchError: ('After 10 seconds test failed: %s', '1 is not < 0')


======================================================================
FAIL: test_keynav_prev_selection_works (unity.tests.test_quicklist.QuicklistKeyNavigationTests)
unity.tests.test_quicklist.QuicklistKeyNavigationTests.test_keynav_prev_selection_works
----------------------------------------------------------------------
_StringException: Empty attachments:
  unity-log

test-log: {{{
11:42:07.720 INFO __init__:69 - Checking system state for badly behaving test...
11:42:09.434 INFO __init__:111 - Test was well behaved.
11:42:09.440 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_quicklist.py", line 207, in setUp
    self.assertThat(icon_refresh_fn, Eventually(Equals(None)))
MismatchError: ('After 10 seconds test failed: %s', 'None != <BamfLauncherIcon gedit.desktop id=24>')


======================================================================
FAIL: test_unhide_single_app (unity.tests.test_showdesktop.ShowDesktopTests)
unity.tests.test_showdesktop.ShowDesktopTests.test_unhide_single_app
----------------------------------------------------------------------
_StringException: test-log: {{{
11:44:00.676 INFO testcase:443 - Starting application 'Character Map' with files [] in locale C
11:44:02.766 INFO testcase:443 - Starting application 'Calculator' with files [] in locale C
11:44:05.167 INFO window_manager:30 - Entering show desktop mode.
11:44:05.168 DEBUG X11:124 - Pressing keys 'Ctrl+Super+d' with delay 0.200000
11:44:05.168 DEBUG X11:208 - Sending press event for key: Control_L
11:44:05.372 DEBUG X11:208 - Sending press event for key: Super_L
11:44:05.575 DEBUG X11:208 - Sending press event for key: d
11:44:05.779 DEBUG X11:142 - Releasing keys 'Ctrl+Super+d' with delay 0.200000
11:44:05.780 DEBUG X11:211 - Sending release event for key: d
11:44:05.985 DEBUG X11:211 - Sending release event for key: Super_L
11:44:06.188 DEBUG X11:211 - Sending release event for key: Control_L
11:44:18.762 INFO __init__:69 - Checking system state for badly behaving test...
11:44:20.656 INFO __init__:111 - Test was well behaved.
11:44:20.662 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{
WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733

WARN  2012-11-26 11:44:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1754135733
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_showdesktop.py", line 68, in test_unhide_single_app
    self.window_manager.enter_show_desktop()
  File "/usr/lib/python2.7/dist-packages/unity/emulators/window_manager.py", line 32, in enter_show_desktop
    self.showdesktop_active.wait_for(True)
  File "/usr/lib/python2.7/dist-packages/autopilot/introspection/dbus.py", line 169, in wait_for
    % (self.parent.__class__.__name__, self.name, failure_msg))
AssertionError: After 10 seconds test on WindowManager.showdesktop_active failed: True != dbus.Boolean(False, variant_level=1)


======================================================================
FAIL: test_launcher_switcher_prev_doesnt_show_shortcuts (unity.tests.launcher.test_switcher.LauncherSwitcherTests)
unity.tests.launcher.test_switcher.LauncherSwitcherTests.test_launcher_switcher_prev_doesnt_show_shortcuts (Single Monitor)
----------------------------------------------------------------------
_StringException: Empty attachments:
  unity-log

test-log: {{{
11:46:04.195 INFO testcase:316 - Setting compiz option 'num_launchers' in plugin 'unityshell' to 0
11:46:05.338 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
11:46:05.349 DEBUG launcher:266 - Starting Super+Tab switcher.
11:46:05.350 DEBUG X11:124 - Pressing keys 'Super' with delay 0.200000
11:46:05.350 DEBUG X11:208 - Sending press event for key: Super_L
11:46:05.553 DEBUG X11:124 - Pressing keys 'Tab' with delay 0.200000
11:46:05.553 DEBUG X11:208 - Sending press event for key: Tab
11:46:05.755 DEBUG X11:142 - Releasing keys 'Tab' with delay 0.200000
11:46:05.755 DEBUG X11:211 - Sending release event for key: Tab
11:46:18.365 INFO testcase:316 - Setting compiz option 'num_launchers' in plugin 'unityshell' to 0
11:46:18.370 INFO __init__:69 - Checking system state for badly behaving test...
11:46:20.148 INFO __init__:111 - Test was well behaved.
11:46:20.153 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
11:46:20.164 WARNING X11:191 - Releasing key 133 as part of cleanup call.
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/launcher/test_switcher.py", line 116, in test_launcher_switcher_prev_doesnt_show_shortcuts
    self.start_switcher_with_cleanup_cancel()
  File "/usr/lib/python2.7/dist-packages/unity/tests/launcher/test_switcher.py", line 34, in start_switcher_with_cleanup_cancel
    self.launcher_instance.switcher_start()
  File "/usr/lib/python2.7/dist-packages/unity/emulators/launcher.py", line 268, in switcher_start
    self._get_controller().key_nav_is_active.wait_for(True)
  File "/usr/lib/python2.7/dist-packages/autopilot/introspection/dbus.py", line 169, in wait_for
    % (self.parent.__class__.__name__, self.name, failure_msg))
AssertionError: After 10 seconds test on LauncherController.key_nav_is_active failed: True != dbus.Boolean(False, variant_level=1)


======================================================================
FAIL: test_alt_f4_doesnt_show_hud (unity.tests.test_hud.HudBehaviorTests)
unity.tests.test_hud.HudBehaviorTests.test_alt_f4_doesnt_show_hud
----------------------------------------------------------------------
_StringException: test-log: {{{
11:46:20.267 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
11:46:20.325 INFO testcase:445 - Starting application 'Calculator' with files []
11:46:23.198 DEBUG X11:124 - Pressing keys 'Alt+F4' with delay 0.050000
11:46:23.199 DEBUG X11:208 - Sending press event for key: Alt_L
11:46:23.252 DEBUG X11:208 - Sending press event for key: F4
11:46:23.304 DEBUG X11:142 - Releasing keys 'Alt+F4' with delay 0.050000
11:46:23.304 DEBUG X11:211 - Sending release event for key: F4
11:46:23.355 DEBUG X11:211 - Sending release event for key: Alt_L
11:46:26.055 DEBUG X11:124 - Pressing keys 'Escape' with delay 0.200000
11:46:26.055 DEBUG X11:208 - Sending press event for key: Escape
11:46:26.259 DEBUG X11:142 - Releasing keys 'Escape' with delay 0.200000
11:46:26.259 DEBUG X11:211 - Sending release event for key: Escape
11:46:26.776 INFO __init__:69 - Checking system state for badly behaving test...
11:46:28.823 INFO __init__:111 - Test was well behaved.
11:46:28.828 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{
WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091

WARN  2012-11-26 11:46:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1522286091
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_hud.py", line 137, in test_alt_f4_doesnt_show_hud
    self.assertFalse(self.hud.visible)
AssertionError: Boolean(True) is not false


======================================================================
FAIL: test_dash_to_hud_has_key_focus (unity.tests.test_hud.HudBehaviorTests)
unity.tests.test_hud.HudBehaviorTests.test_dash_to_hud_has_key_focus
----------------------------------------------------------------------
_StringException: test-log: {{{
11:46:28.943 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
11:46:29.385 DEBUG dash:46 - Toggling dash visibility with Super key.
11:46:29.385 DEBUG X11:124 - Pressing keys 'Super' with delay 0.100000
11:46:29.385 DEBUG X11:208 - Sending press event for key: Super_L
11:46:29.488 DEBUG X11:142 - Releasing keys 'Super' with delay 0.100000
11:46:29.489 DEBUG X11:211 - Sending release event for key: Super_L
11:46:30.390 DEBUG X11:124 - Pressing keys 'Ctrl+a' with delay 0.200000
11:46:30.390 DEBUG X11:208 - Sending press event for key: Control_L
11:46:30.593 DEBUG X11:208 - Sending press event for key: a
11:46:30.796 DEBUG X11:142 - Releasing keys 'Ctrl+a' with delay 0.200000
11:46:30.796 DEBUG X11:211 - Sending release event for key: a
11:46:30.998 DEBUG X11:211 - Sending release event for key: Control_L
11:46:31.199 DEBUG X11:124 - Pressing keys 'Delete' with delay 0.200000
11:46:31.200 DEBUG X11:208 - Sending press event for key: Delete
11:46:31.402 DEBUG X11:142 - Releasing keys 'Delete' with delay 0.200000
11:46:31.402 DEBUG X11:211 - Sending release event for key: Delete
11:46:33.124 DEBUG X11:124 - Pressing keys 'Alt' with delay 0.100000
11:46:33.124 DEBUG X11:208 - Sending press event for key: Alt_L
11:46:33.227 DEBUG X11:142 - Releasing keys 'Alt' with delay 0.100000
11:46:33.228 DEBUG X11:211 - Sending release event for key: Alt_L
11:46:34.000 DEBUG X11:176 - Typing text 'focus2'
11:46:34.000 DEBUG X11:124 - Pressing keys 'f' with delay 0.100000
11:46:34.000 DEBUG X11:208 - Sending press event for key: f
11:46:34.103 DEBUG X11:142 - Releasing keys 'f' with delay 0.100000
11:46:34.103 DEBUG X11:211 - Sending release event for key: f
11:46:34.204 DEBUG X11:124 - Pressing keys 'o' with delay 0.100000
11:46:34.205 DEBUG X11:208 - Sending press event for key: o
11:46:34.307 DEBUG X11:142 - Releasing keys 'o' with delay 0.100000
11:46:34.308 DEBUG X11:211 - Sending release event for key: o
11:46:34.411 DEBUG X11:124 - Pressing keys 'c' with delay 0.100000
11:46:34.411 DEBUG X11:208 - Sending press event for key: c
11:46:34.514 DEBUG X11:142 - Releasing keys 'c' with delay 0.100000
11:46:34.514 DEBUG X11:211 - Sending release event for key: c
11:46:34.616 DEBUG X11:124 - Pressing keys 'u' with delay 0.100000
11:46:34.616 DEBUG X11:208 - Sending press event for key: u
11:46:34.719 DEBUG X11:142 - Releasing keys 'u' with delay 0.100000
11:46:34.719 DEBUG X11:211 - Sending release event for key: u
11:46:34.820 DEBUG X11:124 - Pressing keys 's' with delay 0.100000
11:46:34.821 DEBUG X11:208 - Sending press event for key: s
11:46:34.923 DEBUG X11:142 - Releasing keys 's' with delay 0.100000
11:46:34.924 DEBUG X11:211 - Sending release event for key: s
11:46:35.025 DEBUG X11:124 - Pressing keys '2' with delay 0.100000
11:46:35.025 DEBUG X11:208 - Sending press event for key: 2
11:46:35.127 DEBUG X11:142 - Releasing keys '2' with delay 0.100000
11:46:35.128 DEBUG X11:211 - Sending release event for key: 2
11:46:49.971 DEBUG X11:124 - Pressing keys 'Escape' with delay 0.200000
11:46:49.972 DEBUG X11:208 - Sending press event for key: Escape
11:46:50.174 DEBUG X11:142 - Releasing keys 'Escape' with delay 0.200000
11:46:50.175 DEBUG X11:211 - Sending release event for key: Escape
11:46:50.601 INFO __init__:69 - Checking system state for badly behaving test...
11:46:52.398 INFO __init__:111 - Test was well behaved.
11:46:52.404 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

unity-log: {{{ERROR 2012-11-26 11:46:33 unity <unknown>:0 bamf_matcher_get_application_for_window: assertion `BAMF_IS_WINDOW(window)' failed}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_hud.py", line 212, in test_dash_to_hud_has_key_focus
    self.assertThat(self.hud.search_string, Eventually(Equals('focus2')))
MismatchError: After 10 seconds test on SearchBar.search_string failed: 'focus2' != dbus.String(u'', variant_level=1)


======================================================================
FAIL: test_ignore_key_events_on_hud (unity.tests.test_ibus.IBusTestsPinyinIgnore)
unity.tests.test_ibus.IBusTestsPinyinIgnore.test_ignore_key_events_on_hud
----------------------------------------------------------------------
_StringException: Empty attachments:
  unity-log

test-log: {{{
11:46:52.981 DEBUG X11:124 - Pressing keys 'Alt' with delay 0.100000
11:46:52.982 DEBUG X11:208 - Sending press event for key: Alt_L
11:46:53.084 DEBUG X11:142 - Releasing keys 'Alt' with delay 0.100000
11:46:53.085 DEBUG X11:211 - Sending release event for key: Alt_L
11:46:53.775 DEBUG X11:176 - Typing text 'a'
11:46:53.775 DEBUG X11:124 - Pressing keys 'a' with delay 0.100000
11:46:53.775 DEBUG X11:208 - Sending press event for key: a
11:46:53.878 DEBUG X11:142 - Releasing keys 'a' with delay 0.100000
11:46:53.879 DEBUG X11:211 - Sending release event for key: a
11:46:56.561 DEBUG X11:124 - Pressing keys 'Escape' with delay 0.200000
11:46:56.562 DEBUG X11:208 - Sending press event for key: Escape
11:46:56.764 DEBUG X11:142 - Releasing keys 'Escape' with delay 0.200000
11:46:56.765 DEBUG X11:211 - Sending release event for key: Escape
11:46:57.177 INFO __init__:69 - Checking system state for badly behaving test...
11:46:58.964 INFO __init__:111 - Test was well behaved.
11:46:58.969 DEBUG X11:292 - Moving mouse to position 720,450 without animation.
}}}

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_ibus.py", line 208, in test_ignore_key_events_on_hud
    self.activate_ibus(self.hud.searchbar)
  File "/usr/lib/python2.7/dist-packages/unity/tests/test_ibus.py", line 79, in activate_ibus
    self.assertThat(widget.im_active, Equals(False))
MismatchError: False != Boolean(True)


----------------------------------------------------------------------
Ran 461 tests in 5784.978s

FAILED (failures=80, errors=10, skipped=62)
dale@dale-desktop:~$ B

```

[http://packages.qa.ubuntu.com/qatracker/milestones/246/builds/28425/testcases/1466/results](http://packages.qa.ubuntu.com/qatracker/milestones/246/builds/28425/testcases/1466/results)

So a "bot" will do it all?

The proof is in the pudding so we'll have to wait and see if this improves the quality of our final releases or not.

My bet is on NOT!

Mostly because I think this procedure will discourage individual testing so more testing will be done only in VM's :(

Right now it's time to wait and see.

---

### Post by ventrical on 2012-11-26
> **kansasnoob said:**
> So a "bot" will do it all?

The proof is in the pudding so we'll have to wait and see if this improves the quality of our final releases or not.

My bet is on NOT!

Mostly because I think this procedure will discourage individual testing so more testing will be done only in VM's :(

Right now it's time to wait and see.

Maybe it's just me but I just do not get where the q&a/tracker is going with this. Apparently (as reported by Nick) he has had several  reports come in - but, like you, I am just confused as you are. I don't follow how the proceedure is supossed to work, especially after trying out the  Unity AutoPilot test on the tracker. All I got were errors and warnings at the end of the session so, specifically, what I am trying to say is that I am not certain how  this process can glean the require data needed.

  However I must say that I am not an Ubuntu expert of any sort and so perhaps it may be something that I am doing wrong or not doing correctly.

---

### Post by balloons on 2012-11-26
This is a WIP -- expect something more from me (hopefully today) on this. There's some more options for logging and recording failures the unity team has clued me into -- as I said, it's a learning process, but once we get it settled the rest of the autopilot tests should go smoother. 
[B][I]
In other words, it's ok to be confused at this point -- we're trying to figure out the best way to let you run and report these results, and well, sometimes you don't know until you try :-)
[/I][/B]
Yes, the whole suite takes a long time, so I'm going to split it up on the tracker, so it's a bit saner. The first feedback from people all pointed this out. FYI, you can run subsets like this:

autopilot run unity.tests.test_switcher.SwitcherTests
autopilot run unity.tests.unity.tests.launcher.test_keynav.LauncherKeyNavTests

Etcetera.

---

### Post by ventrical on 2012-11-26
@guitara

Thanks for your reply guitara. I am sure this new process is just as overwhelming for you as it is some of us. I'll just stand by for now and do my regular tests that I do and wait for more on this as it becomes available.

Regards,
Ventrical

---

### Post by balloons on 2012-11-26
I'll just include a copy of my mailing list post here for relevancy:

> Just an update to talk about the unity autopilot tests I included as part of our testing this week based on feedback from the initial folks who have attempted to run and report results.

First, please don't file bugs against unity for any test failures you may encounter. Because the testsuite is still new, there are some tests that may fail -- don't be alarmed if you have many failures. In order to generate useful data, I will be manually collating the testing data from this week and passing the information along to the unity team. I repeat, please don't file bugs for now -- this won't be helpful to the unity team.

Because the testsuite is so long to run in one sitting, the testcase has been updated to explain how to run sections of the suite, as well as how to log the results from each testcase by attaching a link to your log via paste.ubuntu.com (or your favorite paste site :-) ). For example, I've posted a couple results from me personally running the tests here:

[http://packages.qa.ubuntu.com/qatracker/milestones/246/builds/28425/testcases/1466/results](http://packages.qa.ubuntu.com/qatracker/milestones/246/builds/28425/testcases/1466/results)

Switcher, PASSED:

[http://paste.ubuntu.com/1390078/](http://paste.ubuntu.com/1390078/)

Quicklists, FAILED:
[http://paste.ubuntu.com/1390112/](http://paste.ubuntu.com/1390112/)
Since your not reporting any bugs, you'll have to mark everything as 'passed' (sadface :-( ), so be sure to post your failures in front of the log when you file your results. Longer term, better reporting for these autopilot testcases will be explored, but for now I'm enjoying generating some logs and seeing what autopilot is capable of. Just remember the more people who generate test results, the more work I get to do on collating them.. haha.. Make me sweat!

Nicholas

P.S. Keep the feedback coming. I want to get people familiar with the idea of running these autopilot testcases -- as after all, this cycle we're going to make more :-)

---

### Post by mc4man on 2012-11-26
What's not  exactly clear is whether these tests should be run with the default unity/compiz settings in place.
(do you want results from non-default settings?

With non-default settings some tests may fail where they'd otherwise pass & in a case or 2 will pass when they'd fail on the defaults
 (spread test is one example of both instances.., switch test of the former.

---

### Post by ghane on 2012-11-26
> **ventrical said:**
> Guitara wrote:


"If you are feeling adventurous, you can actually run all the unity testcases like this (this will take a LONG TIME!).                      "

  I am currently running Unity AutoPilot on one of my main installs . How long actually will this test run?

The full test (with errors) took 3800 secs on my 2 year old laptop.

--
Sanjeev

---

### Post by ventrical on 2012-11-27
> **ghane said:**
> The full test (with errors) took 3800 secs on my 2 year old laptop.

--
Sanjeev


Thanks! :)

---

### Post by ventrical on 2012-11-27
> **mc4man said:**
> What's not  exactly clear is whether these tests should be run with the default unity/compiz settings in place.
(do you want results from non-default settings?

With non-default settings some tests may fail where they'd otherwise pass & in a case or 2 will pass when they'd fail on the defaults
 (spread test is one example of both instances.., switch test of the former.

Thats a good point. During the auto test it randomly rotated the cube (no harm done). Actually it was rather entertaining :)  There were some other neat Unity/Compiz features that the autopilot exploited that I was not even aware existed. For example , the app switcher .. it was able to  bring up the Unity Dash. itemize , say, about 4 apps, open them, then minimize on the horizontal cassette, highlite and then present in smooth zoom-up, and send send it back to the cassette , or, (reel). Not really a scrollodex effect but very close.

---

### Post by P-I H on 2012-11-27
I ran the full Unity Autopilot test on a desktop with an AMD 620 CPU.
 
Ran 461 tests in 4877.727s
FAILED (failures=61, errors=9, skipped=63)

It changed input method to Chinese-Pinyin and the Dash is now hard to use.
I hope that will be changed after a reboot.

The Dash was OK after reboot.

---

### Post by balloons on 2012-11-28
> **ventrical said:**
> Thats a good point. During the auto test it randomly rotated the cube (no harm done). Actually it was rather entertaining :)  There were some other neat Unity/Compiz features that the autopilot exploited that I was not even aware existed. For example , the app switcher .. it was able to  bring up the Unity Dash. itemize , say, about 4 apps, open them, then minimize on the horizontal cassette, highlite and then present in smooth zoom-up, and send send it back to the cassette , or, (reel). Not really a scrollodex effect but very close.

Non-default settings may very well break the tests. So will running the tests on non-english locales, etc, etc. The unity testsuite is a work in progress, but it's neat to see what they've been able to do (and what we can also achieve!) by using the tool.

So as for your question, yes go ahead and give me the results from your non-standard setup, but mention it's non-standard. Unless the test failing isn't actually a bug (because you've changed how it should work), it will be useful. Some human input will be needed for this :-) For instance, my hud key isn't ALT -- but the HUD tests should look for the shortcut key I use instead and run the tests that way ideally. Test writing isn't always so straightforward -- good things for us to learn as we go about writing tests as well.

---

