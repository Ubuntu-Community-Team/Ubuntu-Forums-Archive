---
title: "WordPress Stock Quote Sidebar"
date: 2013-02-17
forum: Server Platforms
---

### Post by satimis on 2013-02-17
Hi all,

Re "Stock Quote Sidebar"

```

You can use the plugin in several ways, to generate different lists of stocks in different places.

    Specify a list of symbols in the options page
    To use this approach, simply insert the following code where you want the quotes to appear:
    <?php get_stock_quote(); ?>

    Specify a list of symbols in the php function within your WordPress template
    To use this option, call the same function with the symbols as a parameter:
    <?php get_stock_quote("^IXIC,^GSPC,NOVL,ko,pfe,intc"); ?>

```

Where shall I enter those quotes?  Where is the WordPress template?

The 'Stock Quote Sidebar' is now under 'Secondary Widget Area'

TIA

B.R.
satimis

---

