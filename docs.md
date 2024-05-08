# Start
Every form should start with a simplified form definition.

### HTML
```html
<form action="" method="">
    ...
</form>
```

### sForm
```
!act {action} with {method} sep {separator}
```

Separator is used to separate the values in lines. Default separator is ` ` (space). If you don't want to specify a separator you can write simplified version:

```
!act {action} with {method}
```

### Example
```
!act example.com with POST sep ;
```

or

```
!act example.com with POST
```

to not specify a separator.

# Form Elements

Elements with `+` are described in the documentation.

Elements list:
```html
1. <input>
  1. <input type="button"> +
  2. <input type="checkbox"> +
  3. <input type="color">
  4. <input type="date">
  5. <input type="datetime-local">
  6. <input type="email"> +
  7. <input type="file">
  8. <input type="hidden">
  9. <input type="image">
  10. <input type="month">
  11. <input type="number">
  12. <input type="password"> +
  13 .<input type="radio"> +
  1.  <input type="range">
  2.  <input type="reset">
  3.  <input type="search">
  4.  <input type="submit"> +
  5.  <input type="tel">
  6.  <input type="text"> +
  7.  <input type="time">
  8.  <input type="url">
  9.  <input type="week">
1. <label>
2. <select>
3. <textarea>
4. <button>
5. <fieldset>
6. <legend>
7. <datalist>
8. <output>
```

# 1. Input
## 1.1 Button
### HTML
```html
<input type="button">
```

### sForm
```
!button {value, onclick} {optional: id}
```

To use spaces in the button text, you can use quotes.

I recommend using function names in onclick parameter. If you write `!button Play startPlaying` it will be interpreted as `<input type="button" onclick="startPlaying()">Play</button>`

However, if you want to use JS code instead of a function name, you can use quotes.

### Example
```
!button Start startFunction
```

If you need to use spaces in the button text, you can use other syntax:

```
!button "Press to start" startFunction
```

If you want to use JS code in onclick:

```
!button "Say hello" "alert('Hello!')"
```

## 1.2 Checkbox
### HTML
```html
<input type="checkbox">
```

### sForm
Not checked checkbox:

```
!checkbox {name, value} {optional: id}
```

Checked checkbox:

```
!checkbox + {name, value} {optional: id}
```

### Example
Second checkbox is checked:

```
!checkbox hobby reading
!checkbox + hobby music
```

## 1.3 Color
To be added later.

## 1.4 Date
To be added later.

## 1.5 Local Date
No support planned.

## 1.6 Email
### HTML
```html
<input type="email">
```

### sForm
```
!email {name} {optional: placeholder, id}
```

### Example
```
!email userEmail
```

## 1.7 File
To be added later.

## 1.8 Hidden
To be added later.

## 1.9 Image
To be added later.

## 1.10 Month
No support planned.

## 1.11 Number
To be added later.

## 1.12 Password
### HTML
```html
<input type="password">
```

### sForm Syntax
```
!password {name} {optional: placeholder, id}
```

### Example
```
!password userPassword
```

## 1.13 Radio
### HTML
```html
<input type="radio">
```

### sForm Syntax
```
!radio {name, value} {optional: id}
```

### Example
```
!radio gender male
```

## 1.14 Range
To be added later.

## 1.15 Reset
To be added later.

## 1.16 Search
No support planned.

## 1.17 Submit
### HTML
```html
<input type="submit">
```

### sForm
```
!submit {value} {optional: id}
```

### Example
```
!submit Submit
```

If you need to use spaces in the button text, you can use other syntax:

```
!submit "Click Me!"
```

## 1.18 Phone Number
To be added later.

## 1.19 Text
### HTML
```html
<input type="text">
```
### sForm Syntax
```
!text {name} {optional: placeholder, id}
```
### Example
```
!text userSurname
```

## 1.20 Time
No support planned.

## 1.21 URL
To be added later.

## 1.22 Week
No support planned.

# 2. Label
### HTML
```html
<label for="idOfElement">
```

### sForm
In sForm labels are automatically generated from lines that don't start with `!`. Label will be automatically paired with element that placed after it.

Of course, you can also use your own pairing for the label:
```
!label {for} {label text}
```

### Example
```
This is the label
!label someField This is also the label
```

If there is no matching element after Label, or this element is also a Label, then a Legend element will be created instead of a Label

# 3. Select
### HTML
```html
<select>
  <option value="value1">Option 1</option>
  <option value="value2">Option 2</option>
  <option value="value3">Option 3</option>
</select>
```

### sForm
```
!menu {name} {optional: id}
{option name}:{value}
{option name}:{value}
!menu
```

### Example
```
!menu country
USA:usa
France:france
United Kingdom:uk
Russian Federation:russia
!menu
```
If you want to use the `:` symbol in option names, you can use other version of syntax:
```
!menu time
'10:00':ten
'11:00':eleven
'12:00':twelve
!menu
```

# 4. Textarea
### HTML
```html
<textarea name="message" rows="10" cols="30">
The cat was playing in the garden.
</textarea>
```

### sForm
```
!textarea {name} {optional: cols, rows, id}
```

### Example
```
!textarea userReview 10 30
```

# 5. Button
No support planned.

# 6. Fieldset
### HTML
```html
<fieldset>
  <legend>Personal data:</legend>
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname"><br><br>
  <input type="submit" value="Submit">
</fieldset>
```

### sForm
In sForm you should use `[` to start the Fieldset and `]` to end it.

If you want to specify the Legend of Fieldset, then write it on the line above `[`

### Example
You can use tabulation for convenience.
```
Personal data:
[
  First name:
  !text fname
  Last name:
  !text lname
  !submit Submit
]
```

Of course, it's possible to create nested Fieldsets.

# 7. Legend
### HTML
```html
<legend>Personal data:</legend>
```

### sForm
In sForm, legends are generated automatically when you write a Label in front of a form and write a Label in front of another Label

### Example
```
Please, enter your username
Username:
!text username
Other data:
[
  !text otherData
]
```

In this example `Please, enter your username` will become the Legend element, `Username:` will become the Label element of `!text username` and `Other data:` will become the legend element in Fieldset

# 8. Datalist
No support planned.

# 9. Output
No support planned.
