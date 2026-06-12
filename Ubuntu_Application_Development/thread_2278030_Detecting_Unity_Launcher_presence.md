---
title: "Detecting Unity Launcher presence"
date: 2015-05-13
forum: Ubuntu Application Development
---

### Post by giox0692 on 2015-05-13
Hi to all.
I'm developing a C/GTK+ program which will run on many different linuxes and desktop environments.

In this program I would like to use Dynamic Quiclkists of Unity's Launcher as explained here:
[https://wiki.ubuntu.com/Unity/LauncherAPI](https://wiki.ubuntu.com/Unity/LauncherAPI)

My application, when runnning on *ubuntu, is linked with libunity.

I cannot find a way to check if Unity Launcher is running or not.
How can I detect that Unity Launcher is not available when my application is started on a non unity DE ?
My application needs to know it, so it could use an alternative fallback way to show its menu.

The example in the LauncherAPI page uses Unity.LauncherEntry.get_for_desktop_id(), but this function will never fail in other DE, and my application will never know when to use a fallback mechanism.

I'm also trying with DBUS:
```

        v = g_dbus_connection_call_sync(session,
                "com.canonical.Unity.Launcher",
                "/com/canonical/Unity/Launcher",
                "com.canonical.Unity.Launcher",
                "method?????",
                NULL,
                NULL,
                G_DBUS_CALL_FLAGS_NONE,
                -1,
                NULL,
                &error);

```
But my DBUs knowledge is very poor, and I cannot find documentation on /com/canonical/Unity/Launcher. What method should I try to call ?

Any suggestions ?

Thank you

---

### Post by giox0692 on 2015-05-13
1st self answer: this piece of code seems to do the job
```

#include <gio/gio.h>
gboolean is_unity_launcher_available()
{
    /* Check if we have a unity panel running and ready to
     * accept our Update() commands
     * Returns 0 if launcher is available (via DBus) */

    GDBusConnection *session;
    GVariant *v;
    GError *error;

    session = g_bus_get_sync(G_BUS_TYPE_SESSION, NULL, NULL);

    if (!session) return 1;

    error = NULL;
    v = g_dbus_connection_call_sync(session,
        "com.canonical.Unity.Launcher",
        "/com/canonical/Unity/Launcher",
        "org.freedesktop.DBus.Introspectable",
        "Introspect",
        NULL,
        NULL,
        G_DBUS_CALL_FLAGS_NONE,
        -1,
        NULL,
        &error);

    if (v==NULL) {
        g_object_unref(session);
        return 2;
    }

    g_variant_unref(v);
    g_object_unref(session);
    session = NULL;

    return 0;

}


```

Is it correct to call the Introspect method to check the presence of launcher ?

---

