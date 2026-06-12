---
title: "Indicator in C not working?!"
date: 2016-02-13
forum: Ubuntu Application Development
---

### Post by AqD on 2016-02-13
Hello! I'm trying to write a small hardware indicator in C instead of Python, but somehow it just doesn't show up (stuck in GTK main-loop) while all the python ones work fine. There is no error, no warning or anything, and no object listed in the interactive gtk console except GSettings.

My code is ```

#include <stdio.h>
#include <stdlib.h>

#include <libappindicator/app-indicator.h>

static int main_indicator(int argc, char** argv);

int main(int argc, char* argv[])
{
	return main_indicator(argc, argv);
	return EXIT_SUCCESS;
}

static int main_indicator(int argc, char** argv)
{
	printf("Indicator...\n");
	gtk_init(&argc, &argv);
	//
	AppIndicator* indicator = app_indicator_new("clevo-indicator", "go-jumpx",
			APP_INDICATOR_CATEGORY_HARDWARE);
	g_assert(IS_APP_INDICATOR(indicator));
	app_indicator_set_label(indicator, "Hello", "");
	app_indicator_set_attention_icon(indicator, "indicator-messages-new");
	app_indicator_set_status(indicator, APP_INDICATOR_STATUS_ATTENTION);
	app_indicator_set_ordering_index(indicator, -2);
	app_indicator_set_icon(indicator, "go-jump");
	app_indicator_set_title(indicator, "Clevo");
	gtk_main();
	return EXIT_SUCCESS;
}
// build: gcc test-indicator.c `pkg-config --cflags --libs appindicator3-0.1`

```

Any ideas? I tried appindicator3-0.1 and appindicator-0.1 but both are the same. It's Ubuntu 15.10 on x86-64.

---

### Post by AqD on 2016-02-15
Found the problem - the indicator must have a menu to show up, even an empty one, like
```

app_indicator_set_menu(indicator, GTK_MENU(gtk_menu_new()));

```

---

