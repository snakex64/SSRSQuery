# SSRSQuery
Utility to help query MSSQL reporting server


## Example

    using var cancellationTokenSource = new System.Threading.CancellationTokenSource(TimeSpan.FromMinutes(1));
    var options = new SSRSQuery.SSRSQueryOptions(@"http://serveur_here/ReportServer", "ReportName")
    {
        CancellationToken = cancellationTokenSource.Token,
        FileType = SSRSQuery.FileType.PDF,
        Parameters = new Dictionary<string, object>
        {
            ["ReportParameter"] = aValueHere
        }
    };
    var stream = await SSRSQuery.SSRSQueryClient.DownloadReport_AsStream(options);
