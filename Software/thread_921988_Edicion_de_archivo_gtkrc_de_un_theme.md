---
title: "Edicion de archivo gtkrc de un theme"
date: 2008-09-16
forum: Software
---

### Post by sajnox on 2008-09-16
Hola a todos,

Tengo el siguiente problema (un problemon!!) Luego de un tiempo he logrado adoptar otro tema de escritorio al que me acostumbre (al fin....)

El problema es el siguiente:

En apariencia las cajas de entrada estan en color blanco con texto en negro, pero cuando selecciono un archivo y quiero editar el titulo el texto pasa a blanco y sumado al fondo blanco no puedo ver lo que edito.

Buscando y jugando un poco llegue al archivo gtkrc de la carpeta .themes pero no logro identificar la opcion para la edicion de ese punto en particular.

Les dejo el contenido del archivo gtkrc, y desde ya cualquier ayuda es bienvenida.

Valucha, me imagino que seguis por aca no?

```
# WillIbex
# by Jose Javier Espinoza
# Inspired by the WillWill100 mockup (http://willwill100.deviantart.com/gallery/)
#
#Requires:
#pixmap and clearlooks engine
#gnome 2.22.3
#
#Test it in GNU/Linux Ubuntu Hardy Heron
#
#Based in the following themes:
#
# Clearlooks-DarkLime(base GTK Theme)
# version 0.1
# Hacked by Ulisse Perusin <uli.peru@gmail.com>
# based on theme by Jakub Steiner <jimmac@gmail.com>
#
#AIR Theme (scrollbar)
#Slim Gelatine (menu item selected background)
#by Kim Kahns (http://www.kims-area.com/)
#
#Ibex Will(dark color scheme)
#by  Razumok

#styles
include "scrollbar.rc"

#define tiny icon sizes
gtk-icon-sizes = "gtk-menu=16,16:panel-menu=32,32:panel=16,16"
gtk-icon-sizes = "gtk-button=16,16:gtk-large-toolbar=22,22"

#default color scheme
gtk_color_scheme = "fg_color:#6D6050\nbg_color:#474340\nbase_color:#F7EAA1\ntext_color:#101010\nselected_bg_color:#101010\nselected_fg_color:#43312A\ntooltip_bg_color:#EFDC82\ntooltip_fg_color:#AAA"

#widget class horrors from now on
style "willibex-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15

  GtkScrollbar   ::min_slider_length = 30
  GtkCheckButton ::indicator_size    = 14
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 27

  GtkButton      ::child-displacement-x = 1
  GtkButton      ::child-displacement-y = 1

  WnckTasklist   ::fade-overlay-rect = 1
  
  GtkMenu::vertical_padding = 4
  GtkMenu::horizontal_padding = 3
  xthickness = 1
  ythickness = 1


  fg[NORMAL]        = @fg_color 
  fg[PRELIGHT]      = @fg_color 
  fg[SELECTED]      = @selected_fg_color 
  fg[ACTIVE]        = @fg_color 
  fg[INSENSITIVE]   = darker (@bg_color) 

  bg[NORMAL]        = @bg_color
  bg[PRELIGHT]      = shade (1.02, @bg_color) 
  bg[SELECTED]	     = shade (0.5, @bg_color) 
  bg[INSENSITIVE]   = @bg_color 
  bg[ACTIVE]        = shade (0.9, @bg_color) 

  base[NORMAL]      = @base_color 
  base[PRELIGHT]    = shade (0.95, @selected_bg_color) 
  base[ACTIVE]      = shade (1.1, @selected_bg_color) 
  base[SELECTED]    = shade (1.1, @selected_bg_color) 
  base[INSENSITIVE] = @bg_color  

  text[NORMAL]      = @text_color 
  text[PRELIGHT]    = @text_color 
  text[ACTIVE]      = @text_color 
  text[SELECTED]    = @text_color 
  text[INSENSITIVE] = @bg_color

  engine "clearlooks" 
  {
    menubarstyle      = 0       # 0 = flat, 1 = sunken, 2 = flat gradient
    toolbarstyle      = 1       # 0 = flat, 1 = enable effects
    animation         = FALSE
    style             = GUMMY
    radius            = 3.0
    colorize_scrollbar = FALSE
  }

}


style "willibex-wide" = "willibex-default"
{
  xthickness = 2
  ythickness = 2
}

style "willibex-wider" = "willibex-default"
{
  xthickness = 3
  ythickness = 3
}

style "willibex-button" = "willibex-wider"
{
  bg[NORMAL]        = shade (1.05, @bg_color) 
  bg[INSENSITIVE]   = shade (1.04, @bg_color) 
  bg[PRELIGHT]      = shade (1.20, @bg_color) 
  fg[PRELIGHT]	    = @fg_color
  
}

style "willibex-radiobutton" = "willibex-wider"
{
	  bg[SELECTED]   = @selected_bg_color
}

style "willibex-notebook" = "willibex-wide"
{
  bg[SELECTED]  =  shade (0.8, @selected_bg_color)
  bg[NORMAL] 	=  shade (1.1, @bg_color)
}

style "willibex-tasklist" = "willibex-default"
{
  xthickness = 5
  ythickness = 3
}





# File, Edit ...
style "willibex-menubar-panel" {
  fg[NORMAL]   = "#FFFFFF"
  fg[PRELIGHT] = @selected_fg_color 
  xthickness = 5
  engine "pixmap"
	{

		image
		{
		    function 		= BOX
		    state		= PRELIGHT
		    recolorable 	= TRUE
		    file 		= "Menu/menu_item.png"
		    border 		= { 2, 2, 2, 2 }
		    stretch 		= TRUE
		}
		
	}  
}
# File, Edit ...
style "willibex-menubar"
{
	ythickness = 6
	fg[NORMAL]   = "#FFFFFF"
	fg[PRELIGHT] = @selected_fg_color 
	engine "pixmap"
	{
		# Menu background
		image
		{
		    function 		= BOX
		    state		= NORMAL
		    recolorable 	= TRUE
		    file 		= "Menu/menu_bar.png"
		    border 		= { 2, 2, 2, 2 }
		    stretch 		= TRUE
		}
		image
		{
		    function 		= BOX
		    state		= PRELIGHT
		    recolorable 	= TRUE
		    file 		= "Menu/menu_item.png"
		    border 		= { 2, 2, 2, 2 }
		    stretch 		= TRUE
		}
		
	}  
}


style "willibex-menubar-fix"
{
	fg[NORMAL]   = @fg_color
	bg[NORMAL]   = shade(2.50,@bg_color)
	ythickness = 6
	engine "pixmap"
	{
		# Menu background
		image
		{
		    function 		= BOX
		    state		= NORMAL
		    recolorable 	= TRUE
		    file 		= "Menu/fix_d.png"
		    border 		= { 2, 2, 2, 2 }
		    stretch 		= TRUE
		}
		image
		{
		    function 		= BOX
		    state		= PRELIGHT
		    recolorable 	= TRUE
		    file 		= "Menu/menu_item.png"
		    border 		= { 2, 2, 2, 2 }
		    stretch 		= TRUE
		}
		
	}  
}




#individual menus

style "willibex-menu" = "willibex-default"
{
  xthickness = 0
  ythickness = 0
  bg[NORMAL] = shade (0.6, @bg_color) 
  engine "pixmap"
	{
		# Menu background
		image
		{
		    function 		= BOX
		    recolorable 	= TRUE
		    file 		= "Menu/menu.png"
		    border 		= { 0, 0, 0, 0 }
		    stretch 		= TRUE
		}
	}  
}

style "willibex-menu-item"
{
  xthickness = 0
  ythickness = 3
  #fg[PRELIGHT] = shade (0.5, @bg_color)   
  fg[NORMAL] = shade (0.95, @selected_fg_color) 
  fg[SELECTED]   = @selected_fg_color
  fg[INSENSITIVE]   = @selected_fg_color
  fg[ACTIVE]   = @selected_fg_color
  fg[PRELIGHT]   = @selected_fg_color
  text[PRELIGHT] = shade (0.95, @selected_fg_color) 
  bg[SELECTED] = @selected_bg_color    
  bg[NORMAL] = shade (0.6, @bg_color) #separator
  bg[INSENSITIVE] = shade (0.5, @bg_color) #inactive highlight arrows 
  engine "pixmap"
  	{
  		
  		image 
		{
			function		= HLINE
		 	recolorable		= TRUE
		 	file			= "Menu/menu_separador_.png"
			border			= { 0, 0, 1, 0 }
			stretch			= TRUE
		}
		image
		{
		    function 		= BOX
		    recolorable 	= TRUE
		    file 		= "Menu/menu_item_.png"
		    border 		= { 2, 2, 2, 2 }
		    stretch 		= TRUE
		}
		
  	}
}

style "willibex-frame-title" = "willibex-default"
{
  fg[NORMAL] = lighter (@text_color)
}

style "willibex-tooltips" = "willibex-default"
{
  xthickness = 4
  ythickness = 4
	bg[NORMAL] = @tooltip_bg_color
	fg[NORMAL] = @tooltip_fg_color
  #bg[NORMAL] = shade (1.2, @selected_bg_color)
}

style "willibex-progressbar" = "willibex-wide" 
{
  xthickness = 1
  ythickness = 1
  bg[SELECTED]  = shade (1.1, @selected_bg_color)

}


style "willibex-combo" = "willibex-button"
{
	fg[NORMAL] = @text_color
}

style "willibex-scale" = "willibex-button"
{
	GtkRange::trough-side-details = 1
}	

style "willibex-dialogbutton" = "willibex-button"
{

}

style "willibex-tree" = "willibex-default"
{
  xthickness = 2
  ythickness = 2
  bg[NORMAL] = @bg_color
}



#special case panel menus
style "panel-menu" = "willibex-default"
{
	bg[NORMAL] = @bg_color
}

#nautilus search stripe and other specialties
style "extra-view" {
	bg[NORMAL] = shade (1.2, @selected_bg_color)
	fg[NORMAL] = shade (0.5, @bg_color)  
} 

style "evolution-hack" = "willibex-default"
{
        bg[ACTIVE]   = @selected_bg_color  
        bg[SELECTED] = @selected_bg_color  
        fg[ACTIVE]   = @text_color
        fg[SELECTED] = shade (0.5, @bg_color)
}

style "fspot-photos" = "willibex-default"
{
         base[NORMAL] = shade (0.5, @bg_color)
         fg[NORMAL] = "#000000"
}


style "willibex-treeview-nautilus"
{
	GtkTreeView::even-row-color       = @base_color
	GtkTreeView::odd-row-color        = @base_color
}





# widget styles
class "GtkWidget"    style "willibex-default"
class "GtkButton"    style "willibex-button"
class "GtkScale"     style "willibex-scale"
class "GtkCombo"     style "willibex-button"
class "GtkRange"     style "willibex-wide"
class "GtkFrame"     style "willibex-wide"
class "GtkSeparator" style "willibex-wide"
class "GtkEntry"     style "willibex-wider"
class "GtkNotebook"    style "willibex-notebook"
class "GtkProgressBar" style "willibex-progressbar"
class "GtkScrollbar"   style "scroll"
class "GtkCheckButton" style "willibex-radiobutton"
class "GtkRadioButton" style "willibex-radiobutton"
#class "GtkMenuBar" 		style "willibex-menubar-panel"

widget_class "*<GtkMenu>*"              style "willibex-menu"
widget_class "*<GtkMenuItem>*"          style "willibex-menu-item"
widget_class "*<GtkMenuBar>*"           style "willibex-menubar-panel"
widget_class "*.GtkMenuBar*"    style "willibex-menubar"
widget_class "*Fix*MenuBar*" style "willibex-menubar-fix"
#dialog button
widget_class "*.Gtk*ButtonBox.*Button*" style "willibex-dialogbutton"

#menu stripe (but not on the panel)
class "PanelMenuBar" style "panel-menu"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "willibex-combo"
widget_class "*.GtkCombo.GtkButton"    style "willibex-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "willibex-tasklist" ####willibex-tasklist
widget "gtk-tooltip*" style "willibex-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "willibex-tree"
widget_class "*.GtkCTree.GtkButton" style "willibex-tree"
widget_class "*Nautilus*GtkTreeView*" 	style "willibex-treeview-nautilus"
widget_class "*.GtkList.GtkButton" style "willibex-tree"
widget_class "*.GtkCList.GtkButton" style "willibex-tree"
widget_class "*.GtkFrame.GtkLabel" style "willibex-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "willibex-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "willibex-notebook"

#nautilus search stripe
widget "*.nautilus-extra-view-widget" style:highest "extra-view"

#f-spot stuff
class "__gtksharp_*_IconView" style "fspot-photos"
widget_class "*.__gtksharp_*_PhotoView.*.GtkEventBox*" style "fspot-photos"


# Evolution
widget_class "*GtkCTree*" style "evolution-hack"
widget_class "*GtkList*" style "evolution-hack"
widget_class "*GtkCList*" style "evolution-hack"
widget_class "*.ETree.*" style "evolution-hack"
```

---

### Post by pol666 on 2008-09-16
es un problemon, por que lso colores estan por numero y no poir su cifra real :s

---

### Post by sajnox on 2008-09-16
Yo probe de a uno los colores para ver cuales eran, el tema es que me parece que esta tomando algun valor por default y es lo que quiero cambiar

---

### Post by faktorqm on 2008-09-17
Para mi el problema que tenes ahi es que tenes 2 colores con el mismo color (valga la redundancia) y eso es text_color y selected_bg_color. 
BG seguro se refiere a background, o sea, color de fondo.
Ambos tienen #101010 que es basicamente negro. 
Yo probaria de cambiar lo que te puse aca en rojo:

```
#default color scheme
gtk_color_scheme = "fg_color:#6D6050\nbg_color:#474340\nbase_color:#F7EAA1\n[COLOR="Red"]_**text_color:#101010\nselected_bg_color:#101010**_[/COLOR]\nselected_fg_color:#43312A\ntooltip_bg_color:#EFDC82\ntooltip_fg_color:#AAA"
```

por:

```
#default color scheme
gtk_color_scheme = "fg_color:#6D6050\nbg_color:#474340\nbase_color:#F7EAA1\n[COLOR="Red"]_**text_color:#101010\nselected_bg_color:#F0F0F0**_[/COLOR]\nselected_fg_color:#43312A\ntooltip_bg_color:#EFDC82\ntooltip_fg_color:#AAA"
```

Bueno ahi le puse casi blanco, pero podes probar para ver si es eso primero, si no es lo pones como estaba antes.

Una última observación: en el último parámetro figura "tooltip_fg_color:#AAA" y los colores estan formados por 6 caracteres por decirlo "rapido", al igual que todos los anteriores, y ese tiene solo 3. Se rompio alguna configuracion? se habra "cortado" la escritura por algun motivo? tambien podrias probar de ponerle a ese no se, AAA0FF ya que estamos, eso es color violeta clarito (es para que lo diferencies bien del resto de los colores).

Bueno espero que t haya servido. Salu2!

---

### Post by ruisu on 2008-11-09
#AAA = #AAAAAA
según tengo entendido es algo común si se repiten, por ejemplo
ABC = AABBCC
mas no sirve para los que repiten 3 veces dos caracteres ( ababab != ab )

---

### Post by undiaperfecto on 2008-11-10
a mi me pasa algo rarisimo, debe ser un error de mi theme

[IMG]http://img76.imageshack.us/img76/7231/screenshot1zb7.png[/IMG]

---

