# v0.4.5
- Moved [CmdletBinding()] to the above param. Synopsis was not displaying.

# v0.4.4
- Added `Get-OpenAIEdit`. Given a prompt and an instruction, the model will return an edited version of the prompt. Thank you [Skatterbrainz](https://github.com/Skatterbrainz)

# v0.4.3
- Added `-Method POST` to `Get-OpenAIModeration`. Thank you [Skatterbrainz](https://github.com/Skatterbrainz)

# v0.4.2
- Change `-temperature` default to 0

# v0.4.1
- Thank you to [Pieter Jan Geutjens](https://github.com/pjgeutjens)
    - Added `-temperature` param to `ai` and `copilot`
    - Changed the input type from `int` to `decimal`
    - Changed the range on temperature from [0,1] to [0,2] according to the API documentation

# v0.4.0
- Refactored to use `Invoke-OpenAIAPI` function. This function is used by all the other functions in the module. This allows for a single place to update the API URL and the API Key. 
- Add `Get-*` functions for OpenAI URIs
- Took the function suggestions from [Skatterbrainz](https://github.com/Skatterbrainz) and updated with `Invoke-OpenAIAPI`  the refactor: https://github.com/dfinke/PowerShellAI/pull/30
- Refactored `Get-DalleImage` to use `Invoke-OpenAIAPI`
- Refactored `Get-GPT3Completion` to use `Invoke-OpenAIAPI`

# v0.3.3
- Check if `$result.choices` is not null before trying to access it. Thank you [StartAutomating](https://github.com/StartAutomating)
- Examples added to comment based help in `copilot`. Thank you [Wes Stahler](https://github.com/stahler)
- Add `New-Spreadsheet` script. Creates a new spreadsheet from a prompt. [Check out the code](Examples/Excel/New-Spreadsheet.ps1)
- Added `ConvertFrom-GPTMarkdownTable` function. Converts a markdown table to a PowerShell object. [Check out the code](Public/ConvertFrom-GPTMarkdownTable.ps1)
- Unit tests started
- GitHub Actions in place to run CI/CD

# v0.3.2
- Added `Get-DalleImage`: Given a description, the model will return an image
- Added `Set-DalleImageAsWallpaper`: Given a description, the model will return an image form DALL-E and set it as the wallpaper

# v0.3.1
- Added -max_tokens parameter to the `ai` function

# v0.3.0
- Added `copilot` - Makes the request to GPT, parses the response and displays it in a box and then prompts the user to run the code or not. Check the [README.md](README.md) for me details.

- Added `ai` function:
    - Experimental function enables piping

        ```powershell
        ai "list of planets only names as json"
        ```
    
        ```json
        [
            "Mercury",
            "Venus",
            "Earth",
            "Mars",
            "Jupiter",
            "Saturn",
            "Uranus",
            "Neptune"
        ]
        ```
    
        ```powershell
        ai "list of planets only names as json" |
        ai 'convert to  xml'
        ```

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <Planets>
            <Planet>Mercury</Planet>
            <Planet>Venus</Planet>
            <Planet>Earth</Planet>
            <Planet>Mars</Planet>
            <Planet>Jupiter</Planet>
            <Planet>Saturn</Planet>
            <Planet>Uranus</Planet>
            <Planet>Neptune</Planet>
        </Planets>
        ```        
        
# v0.2.0

- Thank you [Martyn Keigher](https://github.com/MartynKeigher) for your contributions!
    - Added `gpt` as an alias:
    
        ```powershell
        # Get-GPT3Completion "list of planets only names as json"
        gpt "list of planets only names as json"
        ``

    - Added validation for: `temperature`, `max_tokens`, `top_p`, `frequency_penalty`, `presence_penalty`
