### Hi there 👋

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<style>
body {
  background-color:#000;
}

h1, span {
    font-size:30px;
}

.output {
  text-align:left;
  font-family: 'Source Code Pro', monospace;
  color:white;  
}

/* Cursor Styling */

.cursor::after {
  content:'';
  display:inline-block;
  margin-left:3px;
  background-color:white;
  animation-name:blink;
  animation-duration:0.5s;
  animation-iteration-count: infinite;
}
h1.cursor::after {
  height:24px;
  width:13px;
}


@keyframes blink {
  0% {
    opacity:1;
  }
  49% {
    opacity:1;
  }
  50% {
    opacity:0;
  }
  100% {
    opacity:0;
  }
}
</style>

<div class="container">
  <h1 class="output">Sergio's repo 📦 main [$⇣] via 🐍 v3.10.2 on ☁️  (us-east-1) </h1>
  <h1 class="output">$ sudo whois $sergio</h1>
  <div class="output" id="output">
    <h1 class="cursor"></h1>
  </div>
</div>

<script>
  // values to keep track of the number of letters typed, which quote to use. etc. Don't change these values.
var i = 0,
    a = 0,
    isBackspacing = false,
    isParagraph = false;

// Typerwrite text content. Use a pipe to indicate the start of the second line "|".  
var textArray = [
  "[[ $__software_developer ]];", 
  "devops &> enthusiast",
  "python && graphql fanatic",
  "docker || kubernetes || aws sysops engineer",
  "react < gatsby > dev",
  "bigdata --sql --kafka --airflow --nosql",
];

// Speed (in milliseconds) of typing.
var speedForward = 100, //Typing Speed
    speedWait = 1000, // Wait between typing and backspacing
    speedBetweenLines = 1000, //Wait between first and second lines
    speedBackspace = 25; //Backspace Speed

//Run the loop
typeWriter("output", textArray);

function typeWriter(id, ar) {
  var element = $("#" + id),
      aString = ar[a],
      eHeader = element.children("h1"), //Header element
      eParagraph = element.children("p"); //Subheader element
  
  // Determine if animation should be typing or backspacing
  if (!isBackspacing) {
    
    // If full string hasn't yet been typed out, continue typing
    if (i < aString.length) {
      
      eHeader.text(eHeader.text() + aString.charAt(i));
        i++;
        setTimeout(function(){ typeWriter(id, ar); }, speedForward);
      
    // If full string has been typed, switch to backspace mode.
    } else if (i == aString.length) {
      
      isBackspacing = true;
      setTimeout(function(){ typeWriter(id, ar); }, speedWait);
      
    }
    
  // If backspacing is enabled
  } else {
    
    // If either the header or the paragraph still has text, continue backspacing
    if (eHeader.text().length > 0) {    
      eHeader.text(eHeader.text().substring(0, eHeader.text().length - 1));
      setTimeout(function(){ typeWriter(id, ar); }, speedBackspace);
    
    // If neither head or paragraph still has text, switch to next quote in array and start typing.
    } else { 
      
      isBackspacing = false;
      i = 0;
      isParagraph = false;
      a = (a + 1) % ar.length; //Moves to next position in array, always looping back to 0
      setTimeout(function(){ typeWriter(id, ar); }, 50);
      
    }
  }
}
</script>

<!--
**sergiogcx/sergiogcx** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
