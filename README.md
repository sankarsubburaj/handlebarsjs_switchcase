# handlebarsjs_switchcase
Switch case with default and break in Handlebars.js 


Switch case:

Handlebars Template:
<div>
    <h1> 
        {{#switch 'a'}} 
            {{#case 'a'}} A {{/case}} 
            {{#case 'b'}} B {{/case}} 
        {{/switch}}
    </h1>
</div>

Register Helper functions:
Handlebars.registerHelper('switch', function(value, options) {
  this.switch_value = value;
  return options.fn(this);
});

Handlebars.registerHelper('case', function(value, options) {
  if (value == this.switch_value) {
    return options.fn(this);
  }
});

=======================================================================================

Switch case with default:

Handlebars Template:
<div>
    <h1> 
        {{#switch 'a'}} 
            {{#case 'a'}} A {{/case}} 
            {{#case 'b'}} B {{/case}}
            {{#default '188'}} {{/default}}
        {{/switch}}
    </h1>
</div>

Register Helper functions:
Handlebars.registerHelper('switch', function(value, options) {
  this.switch_value = value;
  return options.fn(this);
});

Handlebars.registerHelper('case', function(value, options) {
  if (value == this.switch_value) {
    return options.fn(this);
  }
});

Handlebars.registerHelper('default', function(value, options) {
    return true; ///We can add condition if needs
});

=======================================================================================

Switch case with default and break:

Handlebars Template:
<div>
    <h1> 
        {{#switch 'a'}} 
            {{#case 'a'}} A {{/case}} 
            {{#case 'b'}} B {{/case}} 
            {{#default '188'}} {{/default}}
        {{/switch}}
    </h1>
</div>

Register Helper functions: 
Handlebars.registerHelper('switch', function(value, options) {
  this.switch_value = value;
  this.switch_break = false;
  return options.fn(this);
});

Handlebars.registerHelper('case', function(value, options) {
  if (value == this.switch_value) {
    this.switch_break = true;
    return options.fn(this);
  }
});

Handlebars.registerHelper('default', function(value, options) {
   if (this.switch_break == false) {
     return value;
   }
});
