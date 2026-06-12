---
title: "Gtkmm problem to delete widget"
date: 2012-07-02
forum: Ubuntu Application Development
---

### Post by maestrodenada on 2012-07-02
Hi,

First, sorry for my english...

Second, thanks to try to understand me.

Well, I try to do a program where there are a Gtk::ComboBoxText with the name of different people and a Gtk::Grid where different Gtk::Button. The Button(s) depends the person's schedule selected at ComboBox.

ComboBoxText and Grid are designed in glade file, but Button are created when program is running, I create them in a function that is called when the combobox signal changed is throw.

At the first ejecution the program run successfully, but when I change the person in combobox, the new buttons appear but the old buttons don't disappear. 
The function has this structure:

//First, I (try to) remove all button in grid
    if (num_boton_hora > 0) // num_boton_hora is a integer with the number of button created previously
    { 
       for(int j=0; j< num_boton_hora; j++){
          boton_hora[j]->hide();              / /Don't have any error, but don't work like I want
         boton_hora[j]->remove(); 
         hora->remove(*boton_hora[j]);
         hora->unreference();
           delete boton_hora[j];
       };
       
        delete[] boton_hora;
        num_boton_hora = 0;
    };
    
    // connect to database 
   ...
num_boton_hora = ... // the number of rows in select statement
...
   // Create button news
   ...    
  boton_hora= new Gtk::Button*[num_boton_hora];
  ...
  boton_hora[i]= Gtk::manage(new Gtk::Button(texto));  
  ...
 // Add buttons into grid 
 ...   
  hora->attach(*boton_hora[i],dia,hora_dia,1,1); // hora is a pointer of Gtk::Grid
 ...          
 
    show_all_children();
        
}

I try several things remove, delete,... but I don't make that I want... 
Thanks

---

