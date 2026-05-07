# Bao cao ngan - Day 21 MLOps Lab

## Ket qua thi nghiem

Da chay nhieu cau hinh RandomForest va ghi log bang MLflow. Cau hinh tot nhat duoc chon:

```yaml
n_estimators: 200
max_depth: null
min_samples_split: 2
```

Voi rieng `train_phase1.csv` ban dau, accuracy tot nhat dat khoang `0.6740`, chua vuot nguong deploy `0.70`.

Sau khi thuc hien Buoc 3 va gop them `train_phase2.csv` vao `train_phase1.csv`, kich thuoc tap train tang tu 2998 len 5996 mau. Ket qua huan luyen lai:

| Giai doan | So mau train | Accuracy | F1 score |
|---|---:|---:|---:|
| Buoc 2 / phase1 | 2998 | 0.6740 | 0.6730 |
| Buoc 3 / phase1 + phase2 | 5996 | 0.7440 | 0.7429 |

## Nhan xet

Bo tham so co `max_depth: null` cho phep cay hoc linh hoat hon so voi cac cau hinh bi gioi han do sau 3, 5 hoac 10. Khi bo sung them du lieu moi, mo hinh vuot nguong `accuracy >= 0.70`, nen eval gate trong CI/CD co the cho phep deploy.

## Kho khan va cach xu ly

Nguong `0.70` kha cao khi chi dung 2998 mau ban dau, nen pipeline co nguy co bi chan tai job Eval. Cach xu ly la hoan thanh luong huan luyen lien tuc o Buoc 3: them du lieu moi, cap nhat con tro DVC, day du lieu len cloud storage truoc khi `git push`, sau do de GitHub Actions train lai va deploy model moi.
