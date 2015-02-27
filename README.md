# JQuery/Ajax Quiz

Write your answer below each question. 

### Question 1
(a) What is a click handler? 
A click handler is a function that is invoked at the specified event, in this case, a click on the jquery object. You can use .on('click', andPassTheFunctionYouWant), or .click(). 

(b) Where in your JS file should you put it, and WHY? 
You put it inside the document-ready function so that it can occur after any dependencies on other code is ready. However, you can write the function you will want to call with your event wherever you want (likely in the app namespace) and pass that function along with the click handler - you wouldn't want to do on.('click', function(){}), cause it's sloppy and not reusable, although I suppose you could.

As a somewhat related question, many of my questions these days have to do with how best and most intuitively to organize your code throughout the whole app.

### Question 2
If you get the error `$ is undefined`, what does that mean and what could you do to fix it? 
This means that you don't have access to the jQuery library. Perhaps you don't have jQuery in your filesystem or didn't use it as a script source in your html.

### Question 3
What should go in the `$(document).ready()` part of your JS file? 
It could go wherever as it will still only run once everything is loaded. What matters is what you want to have happen within it, and that is a matter of what you have available in the global scope.

### Question 4
In an AJAX GET request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? 

```
$.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
```
The data represents the data that was served in response to the GET request.
### Question 5
In an AJAX POST request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? (Hint: it's not the same as in Question 4.)

```
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'POST',
    dataType: 'JSON',
    data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } },
  })
  .done(function(data) {
    console.log("success!");
  });
```

It's confusing to use the word data within the .done function because it is not the data that is being sent in the POST request - Anna talked about this yesterday and used the word "results" in its place. But even knowing this I am still confused looking at it because it seems intuitive that the data is the same data as you're sending in the POST request, simply because they are both called data. But if it's not the resulting data either (as that's what I said was the data in the previous question), I don't really know.

### Question 6
Suppose you had the following form in your HTML file. Use jQuery to write a single line of code that takes whatever the user entered in the textbox and saves it to the variable `user_input`. 

```
  <form>
    <p>The dress is:</p><input type="text" id="color">
    <input type="submit" value="Submit" id="submit">
  </form>
```
var $(user_input) = $form.find(["input[id='color']").val();

### Question 7
This code looks like it works, but when you run it, you see that the `UserApp.add_all_users()` function executes but `console.log` displays `undefined`. What's wrong with the code? 

```
UserApp.get_all_users = function() {
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
  UserApp.add_all_users(data);
};

UserApp.add_all_users = function(data) {
  console.log(data);
};
```
I mean, a quick fix is to just pass 'data' in the console.log where it says success, or add another log for the data, if what you're trying to do is display the data. Otherwise it depends on what you want to do, which I can't say is entirely clear. UserApp.all_all_users isn't part of the .done function, for example, so if you wanted to add it you'd have to put it in there.


