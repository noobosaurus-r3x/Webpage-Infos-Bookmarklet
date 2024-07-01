# Webpage Data Extractor Bookmarklet

A simple JavaScript bookmarklet that extracts forms, links, images, and word count from any webpage and displays the information in a new window.

## Features

- **Extract Forms**: Lists all forms with their actions, methods, and input elements.
- **List Links**: Displays all anchor links found on the page.
- **Display Images**: Shows all images with a maximum width for easy viewing.
- **Count Words**: Provides the total word count of the text content on the page.

## Installation

1. Open your web browser.
2. Create a new bookmark.
3. Edit the bookmark and set the URL to the following JavaScript code:

    ```javascript
    javascript:(function(){var forms=document.getElementsByTagName('form');var links=document.getElementsByTagName('a');var images=document.getElementsByTagName('img');var bodyText=document.body.innerText;var wordCount=bodyText.split(/\s+/).filter(function(word){return word.length>0;}).length;var newWindow=window.open('','','width=800,height=600');newWindow.document.write('<html><head><title>Extracted Data</title>');newWindow.document.write('<style>body{font-family:Arial,sans-serif}table{width:100%;border-collapse:collapse;margin-bottom:20px}th,td{border:1px solid #ddd;padding:8px;text-align:left}th{background-color:#f2f2f2}tr:nth-child(even){background-color:#f9f9f9}h2{background-color:#4CAF50;color:white;padding:10px}</style></head><body>');newWindow.document.write('<h2>Forms:</h2>');for(var i=0;i<forms.length;i++){var form=forms[i];newWindow.document.write('<table><tr><th colspan="3">Form '+(i+1)+'</th></tr>');newWindow.document.write('<tr><td>Action</td><td colspan="2">'+(form.action||'N/A')+'</td></tr>');newWindow.document.write('<tr><td>Method</td><td colspan="2">'+(form.method||'get')+'</td></tr>');newWindow.document.write('<tr><th>Name</th><th>Type</th><th>Value</th></tr>');for(var j=0;j<form.elements.length;j++){var element=form.elements[j];var value=element.value||'N/A';if(element.type==='checkbox'||element.type==='radio'){value=element.checked?'on':'off'}newWindow.document.write('<tr><td>'+(element.name||'N/A')+'</td><td>'+(element.type||'N/A')+'</td><td>'+value+'</td></tr>')}newWindow.document.write('</table>')}newWindow.document.write('<h2>Links:</h2><table><tr><th>Link</th></tr>');for(var i=0;i<links.length;i++){newWindow.document.write('<tr><td><a href="'+links[i].href+'" target="_blank">'+links[i].href+'</a></td></tr>')}newWindow.document.write('</table>');newWindow.document.write('<h2>Images:</h2>');for(var i=0;i<images.length;i++){newWindow.document.write('<img src="'+images[i].src+'" style="max-width:100%;display:block;margin-bottom:10px;">')}newWindow.document.write('<h2>Word Count:</h2><p>'+wordCount+' words</p>');newWindow.document.write('</body></html>');newWindow.document.close();})();
    ```

4. Save the bookmark.

## Usage

1. Navigate to any webpage from which you want to extract data.
2. Click on the saved bookmarklet.
3. A new window will open displaying:
   - A list of all forms with their details.
   - All anchor links on the page.
   - All images found on the page.
   - The total word count of the text content.



## Contact

For any questions or suggestions, please open an issue in the GitHub repository.

