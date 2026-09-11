
# Current vs Kyoto

## はじめに

- スルーレート・面積計算は京都側の実装が確認しきれていないため無視してください
- json_comparison/DIFF_json_files_[性能名].txtにその性能のグラフで赤点になっているjsonファイル名を保存しています
- CMRは兵庫先生からの指摘で変わっていますが、この状態から変更を加れば良いと思っています（今は変更前）

## 気になった点
- ibの結果が、9コーナーの真ん中を取る場合と、現行システムの.TFによるネットリストで結果が異なる場合がある
- CMR、OVRでは以下の点を変更したらフィットした

変更前  
```
.PRINT V(out1,os) V(out2,os)
+ PAR'1-ABS(V(out1,os))/(0.5*V(in1))' PAR'1-ABS(V(out2,os))/(0.5*V(in1))'
```

変更後(ABSの追加)  
```
.PRINT V(out1,os) V(out2,os)
+ PAR'ABS(1-ABS(V(out1,os))/(0.5*V(in1)))' PAR'ABS(1-ABS(V(out2,os))/(0.5*V(in1)))'
```


## 比較結果

- 横軸が現行システムの結果（頂いているjsonデータの中身）、縦軸が京都システムの結果
- 緑点が「一致している」、赤点が「異なっている」
- 現行システムの結果に対して、変化量が1%未満であれば有効数字・丸め誤差と判断し、「一致している」と評価


![消費電流](json_comparison/values.ib__vs__results.ib_tt.png)

![消費電力](json_comparison/values.ibr__vs__results.ibr.png)

![出力抵抗](json_comparison/values.ro__vs__results.rosim.png)

![直流利得](json_comparison/values.dcgain__vs__results.dcgain_db.png)

![位相余裕](json_comparison/values.pm__vs__results.pm.png)

![利得帯域幅積](json_comparison/values.gbp__vs__results.gbw.png)

![入力換算雑音](json_comparison/values.irn__vs__results.irn.png)

![スルーレート](json_comparison/values.sr__vs__results.sr.png)

![全高調波歪](json_comparison/values.thd__vs__results.thd.png)

![同相除去比](json_comparison/values.cmrr__vs__results.cmrr.png)

![電源電圧変動除去比](json_comparison/values.psrr__vs__results.psrr.png)

![同相入力範囲](json_comparison/values.cmr__vs__results.cmir.png)

![出力電圧範囲](json_comparison/values.ovr__vs__results.ovr.png)