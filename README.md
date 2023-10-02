# Input / Output Utility (IO) for C++

wayne::IO is a bunch of tools related to input/output operation.

Access these functions by adding namespace:

<code>wayne::IO::</code>



This utility also relies on the following libraries

- <code>wayne::strUtil::</code>, [Click Here](https://github.com/tlchiu40209/CppToolkit-strUtil)



This utility has some limitation due to the following:

- In <code>log() and logLn()</code>, a built-in function that might exclusively available for <code>gcc</code> is used to obtain the name of the function: <code>\_\_builtin\_FUNCTION()</code>. This may result in compile errors when using on other compilers than <code>gcc</code>.

## Usage

- <code>log(std::string/char* message, bool isError(Optional), bool revealFuncName(Optional), bool timestamping(Optional), std::string custFuncName)</code>
  
  - Providing a log-like output for your program. The output will include:
    
    - The name of the function that called the <code>log()</code> function.
    
    - The time when <code>log()</code> function was called.
  
  - <code>isError</code> is a flag for you to control whether the output should either place to <code>std:cerr</code> or <code>std:cout</code>. Default: <code>false (std::cout)</code>
  
  - <code>revealFuncName</code> is a flag for you to control whether the name of the function that called the <code>log()</code> should be included in the output. Default: <code>true</code>
  
  - <code>timestamping</code> is a flag for you to control whether the time should be displayed when the function <code>log()</code> is called.
  
  - <code>custFuncName</code> is the string for the name of the function calling <code>log()</code>. The default value is <code>\_\_builtin\_FUNCTION()</code>. You can customize the function name as you like.
  
  - Returns <code>void</code>

- <code>logLn(std::string/char* message, bool isError(Optional), bool revealFuncName(Optional), bool timestamping(Optional), std::string custFuncName)</code>
  
  - Acts the same as <code>log()</code>, but it adds <code>std::endl</code> at the end of every output of <code>log()</code>.
  
  - Returns <code>void</code>

- <code>out(std::string/char* message)</code>
  
  - Outputs <code>message</code> to <code>std::cout</code>
  
  - Returns <code>void</code>

- <code>outLn(std::string/char* message)</code>
  
  - Acts the same as <code>out()</code>, but it adds <code>std::endl</code> at the end of every output of <code>out()</code>
  
  - Returns <code>void</code>

- <code>err(std::string/char* message)</code>
  
  - Outputs <code>message</code> to <code>std::cerr</code>
  
  - Returns <code>void</code>

- <code>errLn(std::string/char* message)</code>
  
  - Acts the same as <code>out()</code>, but it adds <code>std::endl</code> at the end of every output of <code>err()</code>

- <code>inSafe(std::string/char* expectingDataType, int amountOfLetters, std::string/char* fromOptions, bool isGetLine = true)</code>
  
  - Acts similar to <code>std::cin</code> with additional criteria for the ease of input and overflow protection. **Please Note:** Though expected data type is provided to the function, it will still either return <code>std::string</code> or <code>char*</code>. You must convert the returned value manually to the data type you would like to use.
  
  - <code>std::string/char* expectingDataType</code>
    
    - It tells <code>inSafe()</code> what data type you are expecting to be inputed. Different data type may trigger different checking mechanism in <code>inSafe()</code>. Currently, it supports the following data types:
      
      - <code>std::string</code>, or <code>string</code>
      
      - <code>char*</code>
      
      - <code>int</code>
      
      - <code>long</code>
      
      - <code>float</code>
      
      - <code>double</code>
  
  - <code>int amountOfLetters</code>
    
    - It tells <code>inSafe()</code> the amount of letters / digits it is going to accept. Any input length that is greater than the defined amount, will be cut.
    
    - To disable the input limitation, set <code>amountOfLetters = 0, or -1</code> 
  
  - <code>std::string/char* fromOptions</code>
    
    - It tells <code>inSafe()</code> the valid input options. Each option should be divided by <code>,</code> without any space in between.
    
    - Example: "apple,banana,citrius"
    
    - If the user didn't input anything that matched, <code>inSafe</code> will return empty string.
  
  - <code>bool isGetLine</code>
    
    - It tells <code>inSafe()</code> to use <code>std::getline()</code> instead of <code>std::cin</code> to obtain input. When <code>isGetLine</code> is set to true, the data type is limited to
      
      - <code>std::string</code> or <code>string</code>
      
      - <code>char*</code>








