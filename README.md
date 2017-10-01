## Subtitle Parser Cross-Platform
SubtitleParser for Cross-Platform, Works on all Xamarin platform (Xamarin.iOS, Xamarin.Android, Xamarin.Forms) and UWP.
thanks to AlexPoint.

Install via NUGET:
```csharp
Install-Package YunusEfendi.SubtitleParser
```

Supported format:
- MicroDvd
- SubRip
- SubStationAlpha
- SubViewer
- TTML
- WebVTT
- Youtube specific XML format (still in development, contribution pleased :) )

How to Use:
# UWP
```csharp
async Task<StringBuilder> GetSubtitleText(StorageFile storageFile, Encoding encoding)
{
    var sb = new StringBuilder();
    var parser = new SubtitlesParser.Classes.Parsers.SrtParser();
    // note : use SubtitlesParser.Classes.Parsers.SubParser() if you don't specift the format
    using (var stream = await storageFile.OpenStreamForReadAsync())
    {
        var items = parser.ParseStream(stream, encoding);
        foreach (var i in items)
        {
            foreach (var line in i.Lines)
            {
                sb.AppendLine(line);
            }
            sb.AppendLine();
        }
    }
return sb;
```